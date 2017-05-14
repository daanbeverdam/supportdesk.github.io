---
layout: 2column
title: Magento 1.8 "form_keys" impact on FPC
url: magento-1-8-form-keys-impact-on-fpc
description: Magento 1.8 "form_keys" impact on FPC
image: magento-1-8-form-keys-impact-on-fpc
authorimage: Melvyn Sopacua
authorname: Melvyn Sopacua
datePublished: 2013-10-11 07:59:59.000000000 +00:00
dateModified: 2013-10-22 13:26:06.000000000 +00:00
intro: Magento 1.8 "form_keys" impact on FPC
hits: 15122
nav: Blog
---
<h3>Magento 1.8 Form Keys</h3>
<p>Since the beginning of time Magento's backend contained a form key that protected against XSS attacks [1]. With <strong>Magento 1.8</strong> the form key has entered the frontend for pretty much the same reason: to protect against form submission from another website, using your browser. A malicious attacker can add stuff to your cart while you're in a different browser tab or even complete an order for you. This relies on predictable URLs, because the site will not have access to the actual HTML content in the browser tab where you have your Magento order waiting. Everything sent to the Magento store will however submit your cookies and thus use your session.</p>
<h3>Enter the form key</h3>
<p>By adding a unique key to each form or to each link that generates an action on the server, the URL or form content becomes no longer predictable. The form key is stored in the session data and validated upon submission to the server. If they don't match - you get a form key error and the action is not completed.</p>
<p>The way it is implemented in Magento 1.8 is not straight-forward for most of the <strong>Magento FPC implementations</strong> out there and will generate form key errors, because by default they will cache the pages containing the form key of the user that first requested the page and caused it to be stored in the full page cache.</p>
<h3>Magento frontend implementation</h3>
<p>First of all, the form key is not a separate block which can be excluded from FPC. And to make things worse, it's part of top level pages you will want to cache, like categories and product detail and even the homepage if it contains "add to cart" links (which most homepages out there do). For an example, take a look at <strong>app/design/frontend/base/default/template/catalog/product/list.phtml</strong>. You will notice several calls to <strong>$this-&gt;getAddToCartUrl()</strong> which is defined in <strong>app/code/core/Mage/Catalog/Block/Product/Abstract.php</strong>. In there you'll see that unconditionally, the form_key is added to the URL parameters.</p>
<p>On the other hand, using a separate block that would allow FPC implementors to mark it dynamic, would incur a heavy performance penalty, because every link that contains a form_key or form that contains a form_key input element, would have delays for loading and executing the block from a separate file and effectively only outputs sixteen characters fetched from the user's session data.</p>
<h3>But here's the good part</h3>
<p>The good thing is, that a solid FPC implementation should also have code to replace the session ID that is output in some pages with the actual session ID from the currently viewing user. This code can be expanded with a replacement for the form key and this is exactly how Magento Enterprise is doing it.</p>
<p>When a cacheable page is stored in the FPC container, one replaces the form key with a placeholder. After retrieving the stored HTML and before serving the cached page, the placeholder is restored with the form key stored in the user's session or if one does not exist, one should be generated (and subsequently stored in the user's session).</p>
<p>Pages that receive the form key should in general not be cached or at least (partly) tailor to the current user ("dynamic blocks"). This is where the validation code will be called and when done right should no longer generate form key errors.</p>
<h3>Update</h3>
<p>We know of the following FPC implementations who have patched their code:</p>
<ul>
<li><a title="Information about Lesti FPC" href="http://gordonlesti.com/lestifpc/">Lesti FPC</a> as of <a title="Fix for 1.8 Form key" href="https://github.com/GordonLesti/Lesti_Fpc/commit/e3725928fcac1924ed663c33bd4067e99b3e7eb1">this commit </a></li>
<li><a title="Information about Extendware Full Page Cache" href="http://www.extendware.com/magento-extensions/performance/full-page-cache-magento-extension.html">Extendware Full Page Cache</a>, version 1.6.8</li>
</ul>
<p>If you are the maintainer of an FPC implementation or know that an implementation is fixed or not affected, feel free to provide me the details and we'll update the list as soon as possible.</p>
<p>Reference:<br />[1] <a href="http://net.tutsplus.com/tutorials/php/secure-your-forms-with-form-keys/">http://net.tutsplus.com/tutorials/php/secure-your-forms-with-form-keys/</a><a href="http://net.tutsplus.com/tutorials/php/secure-your-forms-with-form-keys/"></a></p>
<p>{snippet meer info}</p>
<p>{snippet melvynsopacua}</p>
<div style="position: absolute; left: -40px; top: 967px; width: 1px; height: 1px; overflow: hidden;" data-mce-bogus="1" class="mcePaste" id="_mcePaste">https://github.com/GordonLesti/Lesti_Fpc/commit/e3725928fcac1924ed663c33bd4067e99b3e7eb1</div>
