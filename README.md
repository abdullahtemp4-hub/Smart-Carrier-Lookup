# Carrier Lookup Smart

**A private Windows research and bulk-extraction tool for motor-carrier data.**

Carrier Lookup Smart helps freight professionals research individual carriers, qualify large carrier lists, and produce practical CSV, HTML, and PDF outputs from live public data services. It runs locally on Windows and opens in a browser, while the distributed executable remains available only through the owner's authorized delivery process.

> **Documentation repository:** This public-facing repository explains the product and its use. It does not publish the executable or the password-protected distribution archive.

## What It Does

- Search by DOT, MC/MX docket, email, phone, officer name, or company name.
- Review identity, authority, insurance, fleet, driver, inspection, and related-company information.
- Run bulk extraction from ranges, pasted lists, or `.txt`, `.csv`, and `.log` files.
- Apply qualification rules for authority, geography, cargo, insurance, fleet, vehicles, drivers, and status.
- Export accepted records as fixed-layout CSV, filterable HTML, or printable PDF reports.
- Keep local session history, report history, cache controls, and an Advance Register for carrier PDFs.

## At A Glance

| | |
|---|---|
| **Platform** | Windows 10 or Windows 11, 64-bit |
| **Delivery** | Authorized users receive a password-protected ZIP |
| **Package** | Executable, product README, and License/EULA |
| **Browser** | Microsoft Edge or Google Chrome |
| **Connection** | Internet access required for live source data |
| **Publisher** | Muhammad Abdullah, trading as HAULIXX LOGISTICS |

## Screenshots

Package contents:

![The distributed package contains the executable, README, and license.](Zip-contains-this.png)

![The executable and its accompanying documents shown together.](Zip-content-Live.png)

## Tutorial

The supplied walkthrough is available here: [Watch the tutorial video](Tutorial-Final.mp4).

The tutorial covers the main search, extraction, filtering, and report workflow. The detailed written tutorial is included in [PROPOSAL.md](PROPOSAL.md) and the distributed package README.

## Data Sources

The application reads live data from public services documented in the product manual, including the US DOT Socrata open-data portal, FMCSA QCMobile when enabled, and NHTSA vPIC for VIN decoding. The linked third-party services remain independent of the product. Data quality, availability, freshness, and rate limits are controlled by those providers.

Carrier Lookup Smart is a research and screening tool. It does not replace official records, compliance review, underwriting judgment, or the user's legal obligations.

## Access And Distribution

The software is proprietary and is not an open-source project. Authorized users receive a separately delivered, password-protected ZIP containing:

```text
Carrier_Lookup_Smart/
├── Carrier_Lookup_Smart.exe
├── README.md
└── License.txt
```

The ZIP is not published in this repository. Do not upload, forward, resell, or share the executable, archive, source code, API keys, or private application data. To request access, another user seat, or a commercial licensing discussion, contact **Muhammad Abdullah / HAULIXX LOGISTICS** using the contact channel provided by the owner.

## Documentation

- [Product proposal and detailed workflow](PROPOSAL.md)
- [Frequently asked questions](FAQS.md)
- [Repository and software license terms](LICENSE)
- [Distribution license supplied with the software](License.txt)

## Requirements Summary

- Windows 10 or 11, 64-bit.
- A modern browser and an internet connection.
- No Python installation or administrator rights required.
- 8 GB RAM recommended; 4 GB is practical for single lookups and small ranges.
- Optional `SOCRATA_APP_TOKEN` and `FMCSA_WEB_KEY` values can improve bulk reliability or enable the FMCSA overlay.

For installation, configuration, complete feature details, limitations, outputs, and data handling, read the [product proposal](PROPOSAL.md) and the README included with an authorized software package.

## Ownership

Carrier Lookup Smart is Copyright (c) 2026 Muhammad Abdullah, trading as HAULIXX LOGISTICS. All rights reserved. See [LICENSE](LICENSE) for the repository terms and the distributed [License.txt](License.txt) for the product EULA.
