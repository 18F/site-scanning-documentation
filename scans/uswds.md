# U.S. Web Design System (USWDS) Scanner

## Summary
A [scan](https://site-scanning.app.cloud.gov/searchUSWDS/) to check each domain for the presence or absence of a USWDS component (i.e. font, style sheet) and the version in use of USWDS.

Specifically, the scan [searches for](https://github.com/18F/domain-scan/blob/tspencer/200scanner/scanners/uswds2.py#L36-L123): presence of `-usa` class in the style sheets, `uswds` in HTML, `.usa-` in HTML, `favicon-57.png` (the USWDS flag) on a website, the fonts used by USWDS (current and former versions) - `Public Sans`, `Source Sans`, and `Merriweather` — `uswds` or `uswds version` or `flavicon-57.png` in CSS. It also searches for the presence of HTML tables, although it uses those as a negative indicator that a site is using USWDS.

* USWDS adoption
* USWDS configuration

## Details

This scanner uses the presence of various elements as votes for or against a site employing USWDS. The use of USWDS is not binary — it's possible to employ limited aspects of the USWDS, since it amounts to a sort of a toolkit — so in practice we shouldn't say whether a site does or does not use USWDS, but instead how "USWDS-y" it is. The effect of this is that a count is returned, rather than a yes/no. The highest counts are around 150, and the floor is set at 0. The mode count is 0. Different elements are weighted differently, e.g. the appearance of the `Source Sans` or `Merriweather` fonts is worth less than the appearance of the `Public Sans` font, because the former two are commonplace, while the latter is bespoke for USWDS.

Scoring is performed slightly differently on the presence of `usa-*` CSS classes — those tags could reasonably appear as few as 10 times or as many as 100+, so those are tallied and the recorded count is based on the square root of the count, e.g. 36 becomes 6, 64 becomes 8, etc. (This is then multiplied by 5, weighting this metric highly.) The idea is to reduce count mobility as the count increases.

There is one scanned-for element that _reduces_ the counts — the presence of `<table>` in the HTML. Every table found on the home page is worth -10 points. At present, no sites using USWDS have a table on their home page.

### USWDS adoption

#### Summary
Detects whether USWDS is in use on an agency website.

#### Relevant Policy
"An executive agency that creates a website or digital service that is intended for use by the public, or conducts a redesign of an existing legacy website or digital service that is intended for use by the public, shall ensure to the greatest extent practicable that any new or redesigned website, web-based form, web-based application, or digital service has a consistent experience - _[21st Century Integrated Digital Experience Act](https://www.congress.gov/bill/115th-congress/house-bill/5759/text)_

#### Stakeholders
* OMB - Automates a part of the compliance review for [21st Century Integrated Digital Experience Act](https://www.congress.gov/bill/115th-congress/house-bill/5759/text)

#### Sample Data File

TBA

### USWDS configuration

#### Summary
Detects whether USWDS is in use on a government website and, if so, what version.

#### Relevant Policy
"An executive agency that creates a website or digital service that is intended for use by the public, or conducts a redesign of an existing legacy website or digital service that is intended for use by the public, shall ensure to the greatest extent practicable that any new or redesigned website, web-based form, web-based application, or digital service has a consistent experience - _[21st Century Integrated Digital Experience Act](https://www.congress.gov/bill/115th-congress/house-bill/5759/text)_

#### Stakeholders
* OMB - Automates a part of the compliance review for [21st Century Integrated Digital Experience Act](https://www.congress.gov/bill/115th-congress/house-bill/5759/text)

#### Sample Data File

TBA

#### Other Notes
* [Human curated list of USWDS sites](https://designsystem.digital.gov/getting-started/showcase/all/)



#### Version Tracking


##### v 0.3

* Added organization field
* Implemented [2nd pass at counting rubric](https://github.com/18F/domain-scan/pull/315)

##### v 0.2

* Fixed bug that was wrongly associating 404 and 500 server codes with 200
* Added domaintype and agency 
* Refined the counting model

##### v 0.1

* The initial rough MVP that we threw together to get started.


