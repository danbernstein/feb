---
title: DC Open Data
author: Dan Bernstein
date: '2018-04-26'
slug: dc-open-data
categories: []
tags:
  - R
  - EDA
  - plotly
  - text mining
description: ''
image: ''
keywords: ''
draft: no
---

The mayor of the District of Columbia [released](https://octo.dc.gov/page/district-columbia-data-policy) a comprehensive data policy in April 2017, calling for the DC government to maintain and periodically update a publically-available inventory of its enterpise datasets, classify the datasets by level of sensitivity, and strategically plan for investment in data infrastructure. The action established a policy of data being open by default, meaning that any efforts to restrict public access to publically-funded data had to provide an explanation. The policy recognized that there are many instances where publically-funded data must be safeguarded and restricted, including for security and federal compliance; section 5 of the policy outlined procedures for appropriately handling sensitive information in light of the open data policy.

This post is just a brief snapshot of the Enterprise Dataset Inventory (EDI), released in March 2018, which serves as a public record of all city datasets, their sensivity classification, and any reasoning for the classification. 

<div>
<h3 style = "text-decoration: underline;text-align: center;">Composition of the Enterprise Dataset Inventory</p>
</h3>
<div>

Nearly one hundred city agencies contributed datasets to the EDI, though the distribution is quite skewed. The Office of the Chief Technology Officer leads the pack, with over 200 entries in the EDI, roughly two-thirds of which are open. DC Public Schools reports the second most datasets, however over one hundred of them are confidential, likely due to federal student privacy policies, such as FERPA. Rounding out the top five are the Department of Transportation (DDOT), the Department of Health, and the Office of Planning. On the other end of the spectrum, more than half of reporting agencies reported less than ten datasets, and over a dozen agencies reported only one dataset. A few agencies of note are the National Geospatial Intelligence Agency, the Architect of the Capitol, and a number of other federal departments and agencies. I would suspect these datasets relate to land holdings within city limits, though some might be more interesting.
<br></br>

<div>
    <a href="https://plot.ly/~danbernstein/9/?share_key=6lk3yTkHBOxU71JMEMH8i2" target="_blank" title="plotly_dcEDI_byclassificationandoffice" style="display: block; text-align: center;"><img src="https://plot.ly/~danbernstein/9.png?share_key=6lk3yTkHBOxU71JMEMH8i2" alt="plotly_dcEDI_byclassificationandoffice" style="max-width: 100%;width: 300px;"  width="300" onerror="this.onerror=null;this.src='https://plot.ly/404.png';" /></a>
    <script data-plotly="danbernstein:9" sharekey-plotly="6lk3yTkHBOxU71JMEMH8i2" src="https://plot.ly/embed.js" async></script>
</div>
<br>


It is also worth examining the degree to which individual agencies released open data versus various degrees of restricted data. By normalizing the data within each agency, we can see the percentage breakdowns for each dataset classification type by agency, and compare across the city government. It is worth noting that after normalizing the data, we can no longer see the number of datasets that each agency reports. However, this plot is in the same order as the first one, so agencies are plotted in decreasing order from left to right. We see that many of the agencies that only reported a single dataset provide that dataset as open data, whereas agencies reporting dozens of datasets produce different mixtures of classified data. Some agencies, such as the attorney general's office and the department of corrections, almost exclusively report restricted confidential data, whereas others, such as DDOT and the Department of Consumer and Regulatory Affairs report almost all of their datasets as open data.
<br></br>


<div>
    <a href="https://plot.ly/~danbernstein/11/?share_key=pSo3nRDjBL8HcryBnSrJZE" target="_blank" title="plotly_dcEDI_byclassificationandoffice_normalized" style="display: block; text-align: center;"><img src="https://plot.ly/~danbernstein/11.png?share_key=pSo3nRDjBL8HcryBnSrJZE" alt="plotly_dcEDI_byclassificationandoffice_normalized" style="max-width: 100%;width: 300px;"  width="300"  onerror="this.onerror=null;this.src='https://plot.ly/404.png';" /></a>
    <script data-plotly="danbernstein:11" sharekey-plotly="pSo3nRDjBL8HcryBnSrJZE" src="https://plot.ly/embed.js" async></script>
</div>

<br>

<div>
<h3 style = "text-decoration: underline;text-align: center;">Assessing Datasets Classification Reasons</p>
</h3>
<div>

<p>To better understand why agencies restrict access to publically-funded data, we can examine the reasons the agencies provided for the dataset classifications. This variable is a text field, rather than a drop-down menu of preset options, so there is a wide variety of reasons, and the words used to describe these reasons also vary. Here, I broke down the reasons field into individual words and the counted the frequency of each word within the various classification types (Open, Public But Not Actively Released, For District Government Use, Confidential, Restricted Confidential). From these counts, I produced wordclouds that let you see the results, where words that appear more frequently are larger and more pronounced. Here, the wordclouds are limited to fifty words per plot and words must appear at least ten times to be included.

<p style="float: right;">
      <img src="/img/blogs/dc open data/wordcloud_Open.png"
      height="200px" width="200px"></p>
<p>
Open: Most of the open datasets do not include any information in the classification reason. Only four words appear more than ten times each in the text field (requested, entities, government, and public). The fact that most open datasets did not include a classification reason indicates that DC's open data policy is open by default. Rather than justifying why each dataset is available to the public, all datasets are public unless a reason is given. </p>
</div>

<div style="clear: right;">
<p style="float: right;">
      <img src="/img/blogs/dc open data/wordcloud_Public Not Proactively Released.png"
      height="200px" width="200px"></p>
<p>
Public But Not Actively Released: With all the other dataset classifications, the reasons field offers insight into what kinds of data is within each classification and what reasons are given to justify restricting access. For datasets that are public but not proactively released, we see words like "administrative", "redaction", "subjective", and "financial". We also see words like "require", "finalized", "authentication" and "disclosure", which might indicate that the information is publically available but it is physically restricted, in that individuals need to submit a form or other documentation to access it. We also see two words, "undue" and "burden", which, if this had been done with bigrams, might have been seen frequently as a term; the datasets in this classification might either require extensive collation before open release, online maintenance might be expensive or time-consuming. There are additional reasons why this information's release would create undue burden. </p>
</div>

<div style="clear: right;">
<p style="float: right;">
      <img src="/img/blogs/dc open data/wordcloud_For District Government Use.png"
      height="200px" width="200px"></p>
<p>
For District Government Use: Here we start to see a number of words that are traditionally used when discussing government data, like "foia", which stands for Freedom of Information Act, "trade", "exemptions", and "secret". These words indicate that these datasets might contain information that is proprietary or contains other information that is exempted from open data policies for one reason or another.</p>
</div>

<div style="clear: right;">
<p style="float: right;">
      <img src="/img/blogs/dc open data/wordcloud_Confidential.png"
      height="200px" width="200px"></p>
<p>
Confidential: The Confidential datasets include words related to personally identifiable information (PII). Beyond actually containing the acronym ("pii") and each of the words, we see words related to individuals, such as "health", "student", "educational", and "ferpa". The Family Educational Rights and Privacy Act of 1974 (FERPA) governs the privacy of student educational records in all institutions receiving public funding.   
</p>
</div>

<div style="clear: right;">
<p style="float: right;">
      <img src="/img/blogs/dc open data/wordcloud_Restricted Confidential.png"
      height="200px" width="200px"></p>
<p>
Restricted Confidential: In the most restricted dataset classification, we see terms applicable to essential public services that, if disrupted, would create high levels of chaos. These words are "infrastructure", "safety", "enforcement"; these datasets might relate to law enforcement and critical information about public utilities. We see words conveying the seriousness of these datasets ("injury", "major", "damage", "critical", "sensitive"). Finally, we also see a number of terms that are seen in other classifications, such as "pii and "privacy", which might indicate some issues in the classification system. Is there a legitimate reason why a dataset containg PII would be placed in the highly-classified "restricted confidential" group rather than just simply classified?  </p>
</div>

