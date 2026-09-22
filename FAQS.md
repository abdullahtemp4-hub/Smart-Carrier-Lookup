# Frequently Asked Questions

## General

<details>
<summary>What is Carrier Lookup Auto?</summary>

Carrier Lookup Auto is a private Windows application for researching individual motor carriers, processing carrier lists in bulk, applying qualification rules, and exporting CSV, HTML, and PDF reports. It can create 1000s of Leads in seconds.

</details>

<details>
<summary>Who is it designed for?</summary>

It is designed for freight brokers, dispatchers, carrier-compliance and onboarding teams, insurance and factoring professionals, and other users who research or qualify motor carriers at volume.

</details>

<details>
<summary>What can I search for?</summary>

You can search by DOT number, MC/MX/FF docket number, email, phone, officer name, or company name. Automatic type detection is also available.

</details>

<details>
<summary>Does it get data from its own datasets?</summary>

No. Carrier Lookup Auto does not contain its own offline carrier dataset. It retrieves carrier information live from the documented public data services, primarily US DOT Socrata datasets and, when enabled, the FMCSA QCMobile API. NHTSA vPIC is used separately for VIN decoding.

The application may temporarily cache source responses locally when caching is enabled, but these cached responses are not the application's own carrier dataset or an independent source of record.

</details>

## Installation & Requirements

<details>
<summary>Which operating systems are supported?</summary>

The documented build supports Windows 10 and Windows 11, 64-bit. It is a Windows-only application and is not documented as supporting macOS or Linux.

</details>

<details>
<summary>Do I need Python?</summary>

No. The portable executable is self-contained and includes its required dependencies. A separate Python installation is not required.

</details>

<details>
<summary>Do I need administrator rights?</summary>

No. Administrator rights are not required.

</details>

<details>
<summary>Which browser should I use?</summary>

Use a modern browser such as Microsoft Edge or Google Chrome. The application starts a local web server at `http://127.0.0.1:8000` by default and opens the interface automatically.

</details>

<details>
<summary>Do I need an internet connection?</summary>

Yes. Carrier data is fetched live from the documented public data services. Carrier Lookup Auto does not include an offline copy of the carrier data.

</details>

<details>
<summary>Are API keys required?</summary>

No. `SOCRATA_APP_TOKEN` is optional but strongly recommended, particularly for bulk extraction. `FMCSA_WEB_KEY` is also optional and enables the additional FMCSA overlay when the FMCSA feature is switched on.

</details>

## Download & Package

<details>
<summary>Is the executable included in the documentation repository?</summary>

The executable is distributed separately from the documentation. The authorized distribution package contains the portable executable and the required documentation and licence files.

</details>

<details>
<summary>What is inside the distributed package?</summary>

The documented distribution folder contains:

```text
Carrier_Lookup_Smart.zip/
├── Carrier_Lookup_Smart.exe
├── README.md
└── License.txt
```

Runtime files such as `.env`, `data/`, and `logs/` are created automatically when the application is used.

</details>

<details>
<summary>Is the software portable?</summary>

Yes. Carrier Lookup Auto is distributed as a portable executable. No installer or registry installation is required. To uninstall it, close the application and delete its folder.

</details>

<details>
<summary>How do I request access or another user licence?</summary>

Contact Muhammad Abdullah at [abdullahtemp4@gmail.com](mailto:abdullahtemp4@gmail.com). Access, additional user licences, and licence transfers are subject to the proprietary licence terms.
</details>


## Features

<details>
<summary>Can I process many carriers at once?</summary>

Yes. Bulk extraction accepts a numeric DOT or MC range, a pasted list, or an uploaded `.txt`, `.csv`, or `.log` file. Duplicate identifiers in pasted or uploaded lists are removed automatically.

</details>

<details>
<summary>What search and carrier information can be displayed?</summary>

Carrier records can include legal and DBA names, docket numbers, entity type, physical and mailing addresses, officers, email and phone numbers, operating authority, insurance, USDOT status, cargo classifications, fleet and driver counts, inspections, VINs, related companies, safety information when enabled, and source errors where applicable.

</details>

<details>
<summary>Which reports can I export?</summary>

Bulk runs produce a fixed 56-column CSV and a self-contained HTML report. The application also provides PDF daily-register output. Search results currently displayed on the Search page can be exported to HTML or PDF.

</details>

<details>
<summary>Can I filter bulk extraction results?</summary>

Yes. Rules can filter by entity type, operation classification, country, states, cargo categories, company and officer keywords, authority level, insurance age, fleet size, vehicle counts, driver counts, active USDOT status, and active insurance.

The Rules page also provides presets such as the 48 contiguous states and 50-state selection.

</details>

<details>
<summary>Can I stop a bulk extraction while it is running?</summary>

Yes. **Stop Extraction** cancels the running job cleanly. Records that have already been written to disk remain available. It may sometimes not work.

</details>

<details>
<summary>Does the application save extraction sessions?</summary>

Yes. Each run is stored in a local SQLite session database with its status, progress, counters, timings, and event log.

</details>

<details>
<summary>Does the application have caching?</summary>

Yes. Carrier-detail results are cached locally for up to five days, and search history is retained for 24 hours. An optional source-response cache can also be enabled through `SOURCE_CACHE_TTL_HOURS`.

</details>
<details>
<summary>Can I view HTML and PDF reports offline?</summary>

Yes. Once generated, HTML reports can be opened offline in a modern web browser because they are self-contained, with their styling embedded in the file. PDF reports can also be viewed offline using a PDF reader.

An internet connection is only required for functions that retrieve or process live carrier data from the public data services.

</details>


<details>
<summary>Can I decode VINs?</summary>

Yes. Individual VINs observed during inspections can be decoded through the NHTSA vPIC service to retrieve information such as make, model, and model year.

</details>

## Tutorial

<details>
<summary>Where can I watch the tutorial?</summary>

It is given in the repository. Here: [open the tutorial video](https://res.cloudinary.com/dmh3yyu3p/video/upload/v1790111260/Tutorial-Final_uvdtz5.mp4) The README contains the complete written product documentation.

</details>


## Data & Processing

<details>
<summary>Where does the carrier data come from?</summary>

Carrier Lookup Auto reads data from the documented public services, including US DOT Socrata datasets and, when enabled, the FMCSA QCMobile API. NHTSA vPIC is used separately for VIN decoding.

The application also provides outbound links to services such as Safer, Fleetfax, BrokerSnapshot, and Motus, but it does not scrape or read those websites.

</details>

<details>
<summary>Does the application include an offline carrier database?</summary>

No. Carrier data is fetched live from the documented public services. Local caching can reuse previously fetched responses, but the application does not provide an offline source of carrier data.

</details>

<details>
<summary>What happens if a government data source is slow or unavailable?</summary>

Public data services may become slow, throttle requests, change their schemas, or become temporarily unavailable. Where possible, affected source problems are recorded in `source_errors`. The application cannot guarantee the availability, completeness, accuracy, or freshness of upstream data.

</details>

<details>
<summary>Does the FMCSA overlay work in bulk extraction?</summary>

The FMCSA QCMobile API does not provide a batched form. Therefore, bulk extraction is generally intended to use the batched Socrata engine, while the FMCSA overlay can be switched on when the additional FMCSA information is needed. Most of the details can be fetched in bulk, as seen in the tutorial video.

</details>


## Privacy & Local Data

<details>
<summary>Where are API keys stored?</summary>

API keys are stored in a `.env` file beside the executable. The file should be treated as confidential and must not be shared, uploaded, or included in screenshots or support requests.

</details>

<details>
<summary>Does the application send my data to the owner's server?</summary>

No, The application is documented as a local application that communicates directly with the listed public data services. By default, its local server binds to `127.0.0.1`, meaning it is accessible only from the same computer.

The application does not require an owner's server for its documented carrier-data functions.

</details>

<details>
<summary>Where are my reports and working files stored?</summary>

Application-generated files are stored inside the application folder under `data/` and `logs/`. This includes reports, session history, caches, and operational logs.

Search-page exports are downloaded by your browser and normally go to your browser's Downloads location.

</details>

<details>
<summary>Should I share my `.env`, reports, logs, or session database?</summary>

No. The `.env` file may contain API keys, while reports, logs, and the session database may contain your extracted carrier information and work history. These files should be removed or redacted before sharing screenshots, support material, or copies of the application folder.

</details>

## Security & Network

<details>
<summary>Is the local web server accessible from the internet?</summary>

Not by default. The application binds to `127.0.0.1`, which limits access to the local computer. The product is designed as a single-user local application and should not be exposed to a network or the internet.

</details>

<details>
<summary>Does the application require an administrator account?</summary>

No. Administrator rights are not required for normal operation.

</details>

<details>
<summary>What should I do if Windows shows a SmartScreen or firewall prompt?</summary>

Windows may display a SmartScreen or firewall prompt when the executable is first run. Carrier Lookup Auto works locally on your computer and its server runs on `127.0.0.1`, so the application itself does not expose its local web interface to the network.

</details>


## License & Usage

<details>
<summary>Can I share, resell, rent, or lend the software?</summary>

No. The software is proprietary and licensed to named recipients. The licence does not permit giving, selling, renting, lending, sublicensing, or otherwise transferring the software or a copy of it to another person without the owner's permission.

</details>

<details>
<summary>Can I share the source code?</summary>

No. The source code is confidential and may not be distributed, published, uploaded, or shared under the licence.

</details>

<details>
<summary>Can I reverse engineer or decompile the software?</summary>

The licence prohibits reverse engineering, decompiling, and disassembling except to the extent that such restrictions are not permitted by applicable law.

</details>

<details>
<summary>Can I make a backup copy?</summary>

Yes. The licence permits one backup copy of the installation folder for your own safekeeping.

</details>

<details>
<summary>Can I use the software to provide carrier-lookup services to other people?</summary>

No, not without the owner's prior written permission. The licence is for the licensee's own internal business use.

</details>

<details>
<summary>Can I move the software to another computer that I own?</summary>

Yes, provided the use remains within the licence terms. When moving the application, do not copy `.env`, and remove generated reports, logs, and session data from the transfer copy if they are not intended to be moved.

</details>

<details>
<summary>What happens if the licence terms are breached?</summary>

The licence may be terminated by the owner. Upon termination, the licensee must stop using the software and destroy copies in their possession, subject to applicable law.

</details>

## Data Use & Disclaimer

<details>
<summary>Does Carrier Lookup Auto guarantee that carrier information is accurate?</summary>

Carrier Lookup Auto presents information obtained from third-party public data services and publicly available government datasets. The information may be incomplete, outdated, unavailable, or missing from the underlying source.

</details>


<details>
<summary>Can Carrier Lookup Auto replace official FMCSA records?</summary>

No. It is a research tool and does not replace official FMCSA records or the user's own regulatory, safety, compliance, or underwriting procedures.

</details>

<details>
<summary>Is Carrier Lookup Auto affiliated with FMCSA, US DOT, or NHTSA?</summary>

No. Carrier Lookup Auto is an independent product and is not affiliated with, endorsed by, sponsored by, or connected to FMCSA, the US Department of Transportation, or NHTSA. It is also independent of Motus, Safer, Fleetfax, and BrokerSnapshot.

</details>

<details>
<summary>Who is responsible for complying with data-service terms and applicable laws?</summary>

The user is responsible for complying with the terms of the underlying data services and applicable laws governing their use of the information, including rules applicable to communications with carriers and other business activities.

</details>