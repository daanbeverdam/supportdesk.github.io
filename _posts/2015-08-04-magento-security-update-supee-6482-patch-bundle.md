---
layout: 2column
title: Magento Security Update SUPEE-6482 Patch Bundle
url: magento-security-update-supee-6482-patch-bundle
description: Magento Security Update SUPEE-6482 Patch Bundle
image: magento-security-update-supee-6482-patch-bundle
authorimage: Ray Bogman
authorname: Ray Bogman
datePublished: 2015-08-04 07:56:00.000000000 +00:00
dateModified: 2015-10-22 13:52:41.000000000 +00:00
intro: Magento Security Update SUPEE-6482 Patch Bundle
hits: 1295
nav: Blog
---
<p><a href="index.php?option=com_content&amp;view=article&amp;id=170:magento-security-update-supee-6482-patch-bundle&amp;catid=29:blog&amp;Itemid=121" title="Magento Security Update SUPEE-6482 Patch Bundle"><img src="images/nieuws/securityrelease.jpg" alt="securityrelease" style="margin: 0px 0px 5px 5px; float: right;" height="157" width="157" /></a></p>
<p>Onlangs zijn er 4<span style="text-decoration: underline;">&nbsp;veiligheidslekken</span> in Magento ontdekt en opgelost in een patch <strong>SUPEE-6482</strong>. De lekken zijn aanwezig in alle versies van Magento (1.4/x - 1.9/x), dus zowel <strong>Magento Community</strong> als <strong>Magento Enterprise</strong> shops hebben hiermee te maken. Officieel zijn er alleen patches beschikbaar vanaf 1.4 en hoger, maar Magento geeft aan dat het hier om alle versies gaat. &nbsp;</p>
<h3>Wat zijn de 4 lekken van SUPEE-6482?</h3>
<ul class="check">
<li>
<p>Cross-site Scripting/Cache Poisoning <strong>[Magento Enterprise only]</strong></p>
<ul>
<li>
<p>&nbsp;Mogelijkheid tot het vergaren van oa. credit card informatie middel een aangepaste host header icm aangepast HTML en Javascript code.</p>
</li>
<li>
<p><span style="text-decoration: underline;">CVSS Severity: 9.3 (<span style="text-decoration: underline;">Critical</span>)</span></p>
</li>
</ul>
</li>
<li>Autoloaded File Inclusion in Magento SOAP API<br />
<ul>
<li>
<p>&nbsp;Afhankelijk van de PHP en server configuratie is het mogelijk toegang te krijgen tot de data middels een API SOAP koppeling.</p>
</li>
<li>
<p><span style="text-decoration: underline;">CVSS Severity: 6.5 (Medium)</span></p>
</li>
</ul>
</li>
<li>XSS in Gift Registry Search&nbsp;<strong>[Magento Enterprise only]</strong><br />
<ul>
<li>
<p>&nbsp;Mogelijkheid tot identiteitsdiefstal&nbsp;in de Gift Registry zoek optie door het aanpassen van de cookie.</p>
</li>
<li>
<p><span style="text-decoration: underline;">CVSS Severity: 6.1 (Medium)</span></p>
</li>
</ul>
</li>
<li>SSRF Vulnerability in WSDL File<br />
<ul>
<li>Incorrecte encoding van de API wachtwoord gegevens.</li>
<li>
<p><span style="text-decoration: underline;">CVSS Severity: 5.3 (Medium)</span></p>
</li>
</ul>
</li>
</ul>
<div class="box-hint">Letop: 2 van de 4 issues zijn enkel <strong>Magento Enterprise</strong> only</div>
<h3>Magento 1.9.2.1 update</h3>
<p>Met de komst van de nieuwe <strong>magento security</strong> patches is er ook een nieuwe versie beschikbaar gekomen, namelijk <strong>Magento 1.9.2.1</strong>. Los van de patches zijn hier en daar ook de nodige bugs opgelost.</p>
<p>De volgende onderdelen hebben een update gekregen: Locale, CMS, Static Blocks, Widgets, Compare en de cookie.phtml</p>
<h3>Wat moet ik doen om Magento Security issues te bestrijden?</h3>
<p>Wij raden onze klanten met een Magento webshop de patches te installeren.</p>
<div class="box-warning">Wij doen dat graag voor u. Mail ons via ons <a href="index.php?option=com_content&amp;view=article&amp;id=10&amp;Itemid=130" title="Stel je vraag">supportaanvraagformulier</a> of bel ons op 020 337 59 61.</div>
<p>Via de Magento download website is het mogelijk de&nbsp;<a href="http://www.magentocommerce.com/download" target="_blank" title="Magento Security Patch SUPEE-6482">Magento security patch SUPEE-6482</a>&nbsp;te installeren. Maak altijd eerst een backup van de database en bestanden voor de patch wordt geïmplementeerd.</p>

<p>{snippet meer info}</p>
<p>{snippet raybogman}</p>
