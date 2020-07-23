# U.S. Web Design System Scan

## Summary
The USWDS scan checks each domain for the use of [U.S. Web Design System (USWDS)](https://designsystem.digital.gov/) code and the code version.

Specifically, the scan [searches for](https://github.com/18F/domain-scan/blob/tspencer/200scanner/scanners/uswds2.py#L36-L123): 

* Presence of `-usa` class in CSS
* `uswds` in HTML
* `.usa-` in HTML
* `favicon-57.png` (the USWDS favicon) in HTML and CSS
* Fonts used by USWDS (`Public Sans`, `Source Sans`, and `Merriweather`)
* `uswds` or `uswds version` in CSS

The scanner also searches for the presence of HTML tables, and uses them as a counter indicator.

## Details

USWDS is toolkit of design principles, user experience guidance, and code. Agencies can—and should—adopt USWDS incrementally. Use of USWDS is not binary so we can't definitively say whether a site does or does not use USWDS. 

The scanner uses the presence of various elements as indicators that a site is using USWDS code. It returns an analysis count, not a score or yes/no. The highest counts are around 150, and the floor is set at 0. The mode is 0. Each element is weighted differently. For example, `Source Sans` or `Merriweather` are weighted less than `Public Sans` because they are more common.

The `-usa` CSS classes can appear as few as 10 times or as many as 100+, so the scanner tallies them and records the count  based on its square root (e.g. 36 becomes 6, 64 becomes 8). The scanner then multiples the count by 5 to increase its weight. 

The presence of `<table>` in the home page HTML _reduces_ the counts. Every HTML table found on the home page receives -10 points. 

### USWDS Analysis
Detects how much USWDS code is in use on an agency website.

### USWDS Version
Detects what version of USWDS code is in use on an agency website.

### Relevant Policy
"An executive agency that creates a website or digital service that is intended for use by the public, or conducts a redesign of an existing legacy website or digital service that is intended for use by the public, shall ensure to the greatest extent practicable that any new or redesigned website, web-based form, web-based application, or digital service has a consistent experience - _[21st Century Integrated Digital Experience Act](https://www.congress.gov/bill/115th-congress/house-bill/5759/text)_


### Related Information
* [Curated list of sites using USWDS](https://designsystem.digital.gov/getting-started/showcase/all/)




