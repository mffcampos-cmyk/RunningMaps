# Alternative and complementary open data sources (non-Strava) for an "active-living / liveability" map, as of October 2026

Scope: data a hobby/startup website could legally ingest and publicly display to score areas for running, cycling, walking and general liveability if Strava data is restricted. Each entry gives access method, licence, cost, coverage, granularity and limitations, with URLs. Where a page could not be retrieved or a licence could not be confirmed, that is stated explicitly in the Gaps subsection rather than guessed.

Context that frames everything below: Strava sued Garmin on 30 Sep 2025 over Segments/heatmap patents and API attribution, then voluntarily dismissed the case without prejudice on 21 Oct 2025 ([Bicycle Retailer](https://bicycleretailer.com/industry-news/2025/10/22/strava-drops-suit-against-garmin); [Escape Collective](https://escapecollective.com/strava-drops-lawsuit-against-garmin-after-21-days/)). Garmin then quietly froze new applications to its Connect Developer Program in spring 2026 ([the5krunner, 14 Sep 2026](https://the5krunner.com/2026/09/14/garmin-developer-api-access-paused/)). The whole fitness-platform ecosystem is therefore tightening, not opening.

---

## Key question 1: Other fitness platforms — is there any public aggregate data or API, and do terms allow third-party public display?

### Takeaway
No fitness platform other than Strava offers a programmatically accessible, redistributable aggregate heatmap. Garmin, Komoot, Ride with GPS and Suunto show community heatmaps only inside their own products; their APIs (where they exist at all) are per-user OAuth access to an individual's own workouts, mostly partner/business-only, and several are paused or shutting down in 2026 (Garmin new applications paused; Google Fit REST and legacy Fitbit Web API sunsetting). Building a public "where people run" layer from these platforms is not realistic in 2026.

### Cited Findings

**Garmin Connect**
- Garmin's Connect Developer Program lists five APIs (Health, Activity, Women's Health, Training, Courses). None is a heatmap or aggregate product; the page offers "throttled production access, branding requirements" and currently says only "Stay tuned for more updates on the program." — [Garmin Developers overview](https://developer.garmin.com/gc-developer-program/overview/)
- New applications to the Connect Developer Program have been paused since spring 2026: on 20 May 2026 Garmin cited a "significant redesign and modernisation of the API program and related processes" and could not say when processing would resume; a March 2026 application was still pending on 11 Sep 2026. Existing approved partners continue to work; Connect IQ is unaffected. — [the5krunner, 14 Sep 2026](https://the5krunner.com/2026/09/14/garmin-developer-api-access-paused/); corroborated by [Terra blog](https://tryterra.co/blog/garmin-connect-developer-program-pause)
- The program is governed by the Garmin Connect Developer Program Agreement (PDF) and Garmin API brand guidelines, which require attribution/branding. — [Agreement PDF](https://www8.garmin.com/en-US/GARMINCONNECTDEVELOPERPROGRAMAGREEMENT/GARMINCONNECTDEVELOPERPROGRAMAGREEMENT_EN.pdf); [Brand guidelines PDF](https://developer.garmin.com/downloads/brand/Garmin-Developer-API-Brand-Guidelines.pdf)
- Garmin's community heatmap exists only as "Trendline Popularity Routing" inside Garmin Connect / Edge devices (brighter = more Garmin users active; based on "billions of miles" of rider data; only OSM-based routes get popularity indication; users can opt out in privacy settings). It is not exposed via any API. — [Garmin blog (IT)](https://www.garmin.com/it-IT/blog/trendline-popularity-routing-pedalare-mtb-sicurezza/); [Garmin forum FAQ](https://forums.garmin.com/apps-software/mobile-apps-web/f/garmin-connect-web/162520/faq---segments-heatmap)
- Garmin's July 2025 API partner rules require third-party data attribution; Strava initially refused, then agreed in Oct 2025 after dropping its suit. — [the5krunner](https://the5krunner.com/2025/10/02/strava-sues-its-biggest-partner-garmin-is-this-2-2b-ipo-suicide/); [Escape Collective](https://escapecollective.com/strava-rolls-out-device-attribution-after-dropping-garmin-lawsuit/)

**Komoot (acquired by Bending Spoons, March 2025)**
- Bending Spoons completed its takeover on 20 Mar 2025; reports put layoffs at roughly 85% of the original workforce. — [Sportive](https://sportive.com/2025/03/20/komoot-staff-warned-of-deep-cuts-after-acquisition-by-italian-tech-firm/); [DC Rainmaker](https://www.dcrainmaker.com/2025/05/komoot-team-goodbye.html)
- The official komoot external API (v007) "is only available to partners, who signed a corresponding partner contract. It is prohibited to use the API without such a contract." Endpoints cover a user's tour list/upload/GPX via OAuth2; nothing for heatmaps. Contact partner@komoot.de. — [komoot API docs v007](https://static.komoot.de/doc/external-api/v007/index.html)
- The komoot Global Heatmap is a Premium feature, refreshed monthly from aggregated anonymous activity; personal heatmaps are private. — [komoot support](https://support.komoot.com/hc/articles/9468742939802) (page returned 403 on direct fetch; summarised from search snippet)
- An unofficial open-source scraper notes komoot "does not give independent and small developers access to their API" and relies on email/password login. — [komootHeatmap GitHub](https://github.com/oskarkraemer/komootHeatmap)
- Terra's komoot integration is listed as deprecated. — [Terra](https://tryterra.co/integrations/komoot)

**Ride with GPS**
- RWGPS launched a Global Heatmap in Sep 2020 built from roughly two years of publicly logged trips (private trips and privacy zones excluded), refreshed weekly, available in the web route planner and mobile apps. — [Bikerumor, 2020](https://bikerumor.com/2020/09/29/ride-with-gps-launches-mobile-web-compatible-heatmap-for-better-route-planning/); [Gravelstoke](https://www.gravelstoke.com/gravel-cycling-gear-blog/ride-with-gps-heatmap)
- In May 2024 RWGPS added 7-day and 30-day windows for Premium users (web only); All-Time view is on web and mobile. No API for the heatmap is mentioned. — [Bikepacking.com, 14 May 2024](https://bikepacking.com/news/new-rwgps-heatmaps-2024/)
- Sources conflict on whether the base All-Time heatmap is free or part of paid tiers (one App Store listing says heatmap is an upgraded-subscription feature; another says free). — [App Store](https://apps.apple.com/app/id893687399)

**Suunto**
- Suunto API (apizone.suunto.com): workout FIT files, summary and sampled data, GPS tracks, via OAuth2. "We currently don't offer the API access for personal use" — companies/organisations only, applications reviewed for brand fit; "We do not charge from the use of the API." No aggregate/heatmap product mentioned. — [Suunto API Zone](https://apizone.suunto.com/)

**Polar**
- Polar Open AccessLink (since Oct 2017): free, read-only API to pull a consenting user's Polar Flow data (exercise, daily activity) via OAuth2; developer registers a client in the admin portal. No aggregate data. — [Polar blog](https://www.polar.com/blog/introducing-polar-open-accesslink-api/); [DC Rainmaker](https://www.dcrainmaker.com/2017/10/polar-flow-api-accesslink.html)

**Wahoo**
- Wahoo Cloud API: OAuth 2.0 access to profile, zones, workouts, plans, routes; "Wahoo limits API access to those who request it", applications sit "pending approval"; Sandbox and Production are separate applications. No fees mentioned; no aggregate/heatmap data. — [Wahoo developers](https://developers.wahooligan.com/cloud)
- COROS and Wahoo announced a two-way API integration (April 2026) — a partner-to-partner integration, not a public program. — [COROS press release](https://coros.com/stories/press-release/c/coros-wahoo-partnership)

**COROS**
- No official public/open API was found. Community tools (TypeScript wrapper, rCoros) reverse the private Training Hub backend (teamapi.coros.com) with email/password login; the wrapper itself states "the COROS API is private and unsupported." — [@pinta365/coros](https://github.com/Pinta365/coros); [rCoros](https://cran.r-universe.dev/rCoros/doc/manual.html)

**MapMyRun (Under Armour), Runkeeper (ASICS), Nike Run Club**
- MapMyRun data is reachable via third-party aggregator Terra (per-user consent; carries MapMyRide/Walk/Fitness history under one UA account). — [Terra MapMyRun](https://tryterra.co/integrations/mapmyrun)
- Nike Run Club: no developer API; as early as 2016 runs from the NRC app "aren't made available through the Nike API"; community library node-nikerunclub uses Puppeteer scraping. — [Smashrun blog, 2016](https://blog.smashrun.com/2016/08/24/nike-run-club-sync-issue); [node-nikerunclub](https://npmjs.com/package/node-nikerunclub)
- No information found on an ASICS Runkeeper API (see Gaps).

**Apple Health / HealthKit**
- HealthKit is an on-device iOS framework with no server-side REST endpoint; the only pattern is an iOS app reading HealthKit with explicit user consent and forwarding to a backend. Users can export their own history as XML from the Health app. No aggregate data exists. — [OpenWearables blog](https://openwearables.io/blog/how-to-integrate-apple-health-api-into-your-backend); [RapidDev](https://rapidevelopers.com/retool-integrations/healthkit)

**Google Fit / Fitbit**
- Legacy Fitbit Web API: support ends 30 Sep 2026, API turned off 30 Oct 2026; successor is the server-side Google Health API, whose scopes are "Restricted" and require privacy/security review. — [Google Health API](https://developers.google.com/health/about); [OpenWearables migration guide](https://openwearables.io/blog/fitbit-web-api-shutdown-2026-migration-guide); [Sahha blog](https://sahha.ai/blog/fitbit-api-sunset-migration/)
- Google Fit REST API: supported only to "end of 2026" with no exact shutdown day; Health Connect is on-device Android only. — [Sahha blog, 26 Aug 2026](https://sahha.ai/blog/google-fit-api-sunset-migration/)

**AllTrails / Wikiloc / Relive / Zwift**
- AllTrails: no public developer API found. Its "Public Lands Program" grants a limited licence to agencies/non-profits that manage trails — a partner tool, not data access. Third-party scrapers (Apify) exist but are unsanctioned; a community MCP server is deprecated and flags redistribution of copyrighted content. — [AllTrails PLP terms](https://publiclands.alltrails.com/terms); [DEV scraper post](https://dev.to/crawlerbros/alltrails-scraper-data-driven-trail-discovery-for-businesses-3nbn); [AllTrails MCP server](https://mcpservers.org/hi/servers/srinath1510/alltrails_mcp_server)
- Wikiloc Terms of Use prohibit "robots, spiders or any other mechanism … to access, copy or control any part of the Website" without express prior authorisation, and bar obtaining content by non-customary means; Wikipedia notes bulk download/re-hosting is prohibited. No API. — [Wikiloc terms](https://www.wikiloc.com/wikiloc/terms_en.html); [Wikipedia](https://en.wikipedia.org/wiki/Wikiloc)
- Relive and Zwift: no public aggregate data or open API surfaced in searches (Zwift is indoor/virtual and irrelevant to place scoring).

**Strava Metro (for comparison, since cities are the only route to it)**
- Access is free of charge but limited to organisations that plan/own/maintain active transportation or outdoor recreation infrastructure, approved per project; academic program for non-commercial research. Downloaded data "may not be publicly distributed"; raw counts only inside Licensee Reports; reports shared externally must be submitted to Strava 30 days before publication; data cannot be used for AI/ML without separate agreement; licence lasts one year; Edge Count exports are subject to the OSM licence; Counter Data cannot be exported. — [Strava Metro Terms](https://metro.strava.com/terms); [Metro homepage](https://metro.strava.com/)

### Inferences
- The only fitness-platform heatmaps that exist outside Strava (Garmin Trendline, komoot Global Heatmap, RWGPS Global Heatmap, Suunto app heatmaps) are rendered tiles inside closed products; scraping them would breach ToS and in Garmin's/komoot's case there is no endpoint at all. For a public website they are at best a qualitative benchmark to eyeball, not an ingestible layer.
- Per-user APIs (Polar, Suunto, Wahoo, Garmin when it reopens) could in principle let a website crowdsource its own heatmap from consenting users, but that is a cold-start problem and Garmin/Suunto/komoot restrict access to companies/partners, so a hobby project would likely be refused or stuck in queue.
- Given Strava's 2025 litigation over heatmap patents (filed 2014/2016), any site rendering its own "heat" from crowdsourced GPS should be aware of the patent risk, though commentators expected prior-art challenges (Garmin had heatmaps in 2013). — [BikeRadar](https://www.bikeradar.com/news/strava-sues-garmin-over-segments-and-heatmaps)

### Gaps
- ASICS Runkeeper: no source found on any current developer API or terms.
- Relive: no information found on any API or aggregate data.
- Exact current status of Garmin's heatmap in Connect web (whether still called "Heat Map" vs Trendline) was only available via forum posts, not official docs.
- Whether the RWGPS All-Time heatmap is free for non-subscribers: sources conflict.
- komoot support article on the Global Heatmap returned HTTP 403 on fetch; details rely on a search snippet.
- Garmin Connect Developer Program Agreement PDF was not parsed for clauses on public display of derived aggregates.

---

## Key question 2: Open bike/pedestrian count data (city portals, Eco-Counter, Telraam, national programmes)

### Takeaway
Fixed-counter data is the most legally clean "real activity" signal available: many cities publish hourly Eco-Counter feeds under CC BY/ODbL-style licences (Paris, NYC, Dublin, Berlin, Cambridge MA, Calgary, Queensland), and Telraam citizen sensors offer an open API with 15-minute multimodal counts. The limitation is spatial: counts exist at tens of points per city, not everywhere, so they can calibrate or validate a model but cannot by themselves score arbitrary neighbourhoods. Portugal (Lisbon/Porto) currently has no open automatic-counter dataset.

### Cited Findings

**Eco-Counter (vendor platform behind most municipal counters)**
- Eco-Visio API is REST/JSON for "your count data" (i.e. the customer's own counters), limited to 100 requests/minute and 5,000/day; credentials come from Eco-Counter, so a third party needs the city's cooperation or the city's open-data re-publication. — [Eco-Visio API](https://eco-compteur.com/produits/eco-visio-range/eco-visio-api-2)
- Eco-Counter sells a "Public Web Page / Public Webpage Evo" module that lets a counter owner publish data on a page visitors can open without login, embeddable, with multi-site comparison in the "+" variant. No central public list of such pages was found. — [Eco-Counter communication modules](https://npu.eco-counter.com/produits/eco-visio-range/communication-modules)

**City open-data portals (verified examples)**
- Paris — "Comptage vélo - Données compteurs": hourly bicycle counts per counter from permanent counters on cycle lanes, loaded daily (J-1), rolling 13 months, via the Opendatasoft API/export; licence not named on the dataset page itself (links to "Conditions d'utilisation"). — [Paris Data](https://opendata.paris.fr/explore/dataset/comptage-velo-donnees-compteurs/information/); Eco-Counter's own case study confirms Paris publishes counter data through an open data API — [Eco-Counter blog](https://eco-counter.com/blog/cas-detude-paris)
- New York City — "Bicycle Counts (Historical)" (Socrata id uczf-rk3c): 7,378,266 rows, Eco-Counter-sourced, dates 2012-08-31 to 2026-01-28, columns countid/id/date/counts/status; "As of January 28, 2026, this dataset has been replaced by Bicycle and Pedestrian Counts dataset." Counter locations in a separate "Bicycle Counters" dataset. Accessible via SODA API. — [NYC Open Data metadata JSON](https://data.cityofnewyork.us/api/views/uczf-rk3c.json)
- Dublin region — "Pedestrian and Cycle counter API for Dublin Region": Eco-Counter sensors updating every 15 minutes, with GeoJSON of counter locations; Ireland's related "Active Travel Counts" app data is CC BY 4.0. — [data.gov.ie](https://data.gov.ie/en_GB/dataset/pedestrian-and-cycle-counter-api-for-dublin-region); [Active Travel Counts showcase](https://data.gov.ie/ga/showcase/c9174c65-1d92-4fa2-be56-efee684a922d?format=rdf)
- Berlin — automatic permanent counting stations at 20 points, directional and cross-section totals, refreshed daily to previous day; a 2024 paper confirms Berlin's counter datasets are publicly available. — [Berlin VIZ bike counters](https://viz.berlin.de/en/traffic-in-berlin/bike-counters/); [arXiv 2406.18454](https://arxiv.org/pdf/2406.18454)
- Cambridge, MA — Broadway Eco-Totem counts transferred daily to the city Open Data Portal. — [City of Cambridge](https://www.cambridgema.gov/cdd/transportation/gettingaroundcambridge/bikesincambridge/ecototem)
- Calgary — counter data on the city open data portal (two datasets, some delay). — [yycbike GitHub](https://github.com/Chealion/yycbike)
- Queensland (AU) — "Average Bicycle Counts by day and hour" CSVs from ~15 active-transport sites. — [data.gov.au](https://data.gov.au/data/dataset/average-bicycle-counts-by-day-and-hour/resource/606ee736-8b6a-4442-bc83-dffbfa36e563)
- California — Caltrans bicycle hourly count CSV from vendor video analytics pilots. — [catalog.data.gov](https://catalog.data.gov/dataset/active-transportation-count-dataset)
- Camden (London borough) — weekly counts from two cycle counters. — [Camden Open Data](https://opendata.camden.gov.uk/Transport/Camden-Cycle-Counters-By-Week-May-September-2016/ybrs-wicj)
- London (TfL) — TfL runs annual manual cycle counts at fixed points in inner and outer London since 2015 (spring; autumn in 2020), and a TLRN indicator from 60 automatic counters covering the 5% of roads that are TLRN. The open bucket cycling.data.tfl.gov.uk exists and requires adherence to TfL's transport data terms and conditions, but the directory listing did not render on fetch. — [TfL press release](https://tfl-newsroom.prgloo.com/news/tfl-press-release-outer-london-sees-22-per-cent-rise-in-cycling-as-new-tfl-data-further-highlights-vital-role-of-active-travel-during-the-pandemic); [DfT Find Transport Data](https://findtransportdata.dft.gov.uk/dataset/cycle-flows-on-the-tfl-road-network-177f4b59093); [cycling.data.tfl.gov.uk](https://cycling.data.tfl.gov.uk/)
- Copenhagen — municipality publishes "Trafiktal" reports (PDF) with average daily bike traffic; a 2011 release put a traffic-count spreadsheet under the Danish open public licence. No current opendata.dk dataset was located. — [Trafiktal 2010–2014 PDF](https://kk.sites.itera.dk/apps/kk_pub2/pdf/1603_Gcise4mznA.pdf); [talk-dk 2011](https://lists.openstreetmap.org/pipermail/talk-dk/2011-June/001516.html)
- Amsterdam — bike-related open datasets found are parking, network ("Fietsnetten") and programme data (CC BY 4.0), not counter time series; Dutch national bike counts are offered through the National Access Point (NDW/MMTIS, DATEX II). — [data.overheid.nl Amsterdam](https://data.overheid.nl/en/community/organization/amsterdam); [DATEX II cycling webinar](https://datex2.eu/wp-content/uploads/2023/12/DATEX_II_concl_webinar_9_Cycling_data.pdf)
- Barcelona — Open Data BCN publishes the bike-lane network (CC BY 4.0) and Bicing real-time availability; no permanent counter dataset found. — [Open Data BCN carril bici](https://opendata-ajuntament.barcelona.cat/data/en/dataset/carril-bici/resource/831aa0ab-cf4b-4e8a-9d7f-1b7656cb692a)
- Lisbon — open data includes the cycle network map service (CC BY 4.0) and GIRA bike-share station status (CC BY), but cyclist counts exist only as PDF reports from the IST/CML-Ativos manual count programme (15 locations May 2020, 60 in Oct 2020; annual counts at 60 locations). — [dados.gov.pt Rede Ciclável](https://dados.gov.pt/en/datasets/rede-ciclavel/); [dados.gov.pt GIRA](https://dados.gov.pt/en/datasets/gira-bicicletas-de-lisboa); [CML-Ativos report 2020](https://lisboaparapessoas.pt/wp-content/uploads/2021/01/relatoriocontagensciclistas2020.pdf); [U-Shift IST bike counts](https://ushift.tecnico.ulisboa.pt/projects/project-bike-counts/)
- Porto — no bicycle counter dataset surfaced in any search.

**Telraam (citizen traffic sensors, open API)**
- Low-resolution window camera + AI chip classifies pedestrians (S2 separates strollers), two-wheelers (bikes and motorbikes), cars, heavy vehicles, plus estimated speed distribution and V85 for cars; sends aggregated anonymous counts at 15-minute resolution; data "can be shared … as Open Data." — [What is Telraam](https://telraam.net/en/what-is-telraam)
- Installed base: almost 2,000 V1 devices active in 19 countries at S2 launch, >26 million hours of counts. — [Traffic Technology Today](https://www.traffictechnologytoday.com/news/traffic-counting-categorization/telraam-launches-new-ai-traffic-counting-device.html)
- Licence: third-party client packages state Telraam data is CC BY 4.0 (Python telraam-data; R telraamStats CRAN metadata), while the telraamStats README says CC BY-SA 4.0 — unresolved discrepancy. API is documented on SwaggerHub (telraam-api.net redirects there) and requires a token. — [telraam-data PyPI](https://pypi.org/project/telraam-data/); [telraamStats README](https://archive.linux.duke.edu/cran/web/packages/telraamStats/readme/README.html); [telraam-api.net](https://telraam-api.net/)
- Telraam was awarded "API of the year" (Belgium). — [TML](https://www.tmleuven.be/en/content/Telraam-is-awarded-API-of-the-year)

**US National Bicycle and Pedestrian Documentation Project (NBPD)**
- Joint Alta Planning + Design / ITE effort providing a consistent count methodology; participants email Eco-Counter data to data@bikepeddocumentation.org in exchange for a summary report. No open bulk download was found; it is a methodology and archive, not an open dataset. — [bikepeddocumentation.org](https://bikepeddocumentation.org/); [project description PDF](https://mobikefed.org/files/bicycle-pedestrian-documentation-project-description.pdf)

### Inferences
- A pragmatic design: harvest counter feeds city by city (Opendatasoft/Socrata/CKAN APIs are standard) and use them as ground-truth to calibrate a model built on OSM infrastructure density; Telraam adds pedestrian counts on residential streets that municipal counters miss, but coverage is clustered in Belgium/NL/DE/UK/FR where the project is active.
- For Portugal specifically, expect to rely on OSM, census grids and environmental layers; the only Lisbon activity signal that is open is GIRA bike-share station occupancy, which is a proxy, not a count.
- Licence hygiene: most municipal feeds are CC BY 4.0 or national open licences; TfL requires accepting its own terms; Paris's dataset page does not name the licence, so check "Conditions d'utilisation" (Paris Data generally uses ODbL) before redistribution.

### Gaps
- Paris dataset licence text not confirmed on the dataset page (only linked).
- TfL cycling.data.tfl.gov.uk file listing did not render; dataset names/years/formats unverified.
- Copenhagen, Amsterdam and Barcelona: no current machine-readable counter time series located; absence in search is not proof of absence.
- Telraam official licence page not reachable (telraam.net/en/open-data and /faq returned 404; SwaggerHub returned 404 on fetch); token cost (believed free with account) unconfirmed from a primary source; current device count unknown.
- Eco-Counter: no public directory of cities with public web pages.
- NBPD: no download page confirmed after site redesign.

---

## Key question 3: OpenStreetMap-derived signals and open-source tooling

### Takeaway
OSM is the only truly global, redistributable base for an activity-friendliness score: footway/cycleway density, park/green area, amenity reach and intersection density can be computed anywhere from ODbL data using Geofabrik extracts (daily, per country) plus OSMnx/Pandana, with Overpass only for small ad-hoc queries. The cost is ODbL share-alike on any derived database you publish, and the fact that OSM measures infrastructure, not usage.

### Cited Findings
- OSM data is licensed under ODbL 1.0: you may copy, distribute, transmit and adapt as long as you credit OpenStreetMap and make clear the data is under ODbL; altered/built-upon data may only be distributed under the same licence; OSM cannot provide free tiles/API for third parties (Tile and API usage policies apply). — [openstreetmap.org/copyright](https://www.openstreetmap.org/copyright)
- Geofabrik provides .osm.pbf extracts by continent, country and sub-region, "normally updated every day", ODbL 1.0, with user names/IDs/changeset IDs stripped. — [download.geofabrik.de](https://download.geofabrik.de/)
- Overpass API: read-only query service; main instance overpass-api.de is "currently overloaded"; fair-use guideline under 10,000 queries and 1 GB/day and 10 min processing (divide by 100 for regular use); default 3-minute timeout; recommends planet mirrors or Geofabrik extracts (filtered with osmium) for country-sized extraction; commercial use should use self-hosted or paid servers. — [OSM wiki: Overpass API](https://wiki.openstreetmap.org/wiki/Overpass_API)
- OSMnx (MIT licence): downloads, models, analyses and visualises walking/driving/biking networks, amenities/POIs, building footprints, transit stops, elevation, speeds/travel times and routing from OSM; cite Boeing (2025) Geographical Analysis 57(4) doi:10.1111/gean.70009. — [osmnx.readthedocs.io](https://osmnx.readthedocs.io/en/stable/)
- Pandana performs fast network accessibility queries; Boeing's tutorial pairs it with OSM amenities to visualise walkability ad hoc; OSMnx isochrones at 4.5 km/h for 5–25 min walking reach. — [Geoff Boeing, pandana](https://geoffboeing.com/2017/08/isochrone-maps-osmnx-python/); [Towards Data Science](https://towardsdatascience.com/measuring-pedestrian-accessibility-97900f9e4d56)
- Transform Transport "15min City Score Toolkit": standalone Jupyter notebook (osmnx 1.7.0) and QGIS script scoring walkability by availability of essential services, on Zenodo. — [Zenodo 14231427](https://zenodo.org/records/14231427); [Zenodo 14231353](https://zenodo.org/records/14231353)
- "A Walk across Europe": high-resolution walkability index for Europe using a 15-minute walk isochrone (Valhalla, 5.1 km/h, ~1,275 m). — [arXiv 2504.17897](https://arxiv.org/pdf/2504.17897)
- SEDAC "SDG Indicator 11.7.1: Urban Public Space, Availability and Access, 2023 Release" computes open-public-space access for 8,873 urban centres in 180 countries from OSM public space + WorldPop within 400 m, delineated with GHS-UCDB (DOI 10.7927/eavc-4k45). — [catalog.data.gov](https://catalog.data.gov/dataset/sdg-indicator-11-7-1-urban-public-space-availability-and-access-2023-release)
- Overture Maps (alternative/complement to OSM): Base, Buildings, Divisions, Transportation themes are ODbL ("© OpenStreetMap contributors"); Places are per-source, mostly CDLA Permissive 2.0 (Foursquare Apache 2.0, AllThePlaces CC0); Addresses per-country licences. — [Overture attribution](https://docs.overturemaps.org/attribution/)
- OSM GPS traces and `/api/0.6/trackpoints` are covered under Key question 6.

### Inferences
- Pipeline that respects licences and quotas: download Geofabrik country PBFs (Portugal is a standard Europe sub-region on Geofabrik, though the index page fetched did not list sub-regions), filter with osmium, build OSMnx/Pandana graphs, compute per-hexagon (e.g. H3) metrics: km of highway=footway/cycleway/path per km², park/leisure area share, intersection density, amenity counts within 15-min walk, slope from a DEM. Publish the resulting score grid under ODbL (share-alike) with "© OpenStreetMap contributors".
- r5py (R5 engine, OSM PBF + GTFS) is the right tool if transit accessibility is part of the liveability score; its docs page was unreachable in this session (see Gaps), but the arXiv/Zenodo projects above show walking-only indices do not need it.
- OSM-based indices capture supply (infrastructure) not demand (who actually runs there). That is exactly the gap counter data (Q2) and GPS traces (Q6) fill; the two should be combined rather than substituted.

### Gaps
- r5py documentation returned 404 at the URL tried; its licence and feature set were not verified this session.
- Geofabrik index page did not list per-country sub-regions, so Portugal's separate extract (expected at europe/portugal) was not confirmed from the fetched page.
- Overpass page does not state the licence of returned data explicitly (it is OSM data, hence ODbL, per the copyright page).

---

## Key question 4: Existing liveability indices, census grids and environmental layers — openness and terms

### Takeaway
For Europe there is an unusually rich stack of free, CC BY-licensed layers: Copernicus Urban Atlas/Tree Cover (free and open with attribution), EEA noise contours and air quality (CC BY 4.0), Eurostat 1 km census grid, GHSL population (CC BY 4.0), INE Portugal census grids/BGRI (INE states CC BY 4.0 generally), the EU Quality of Life in European Cities survey microdata (CC BY 4.0), OECD data (open licence since July 2024), OpenAQ (free API, 60 req/min). The proprietary indices are expensive or US/Canada-only: Walk Score API covers US and Canada, free tier for basic scores then from $115/month; Numbeo API from $260/month; Teleport's status is unverified.

### Cited Findings

**Walk Score / Bike Score**
- "The Walk Score API is supported in the United States and Canada"; returns Walk Score, with Bike Score (bike=1) and Transit Score (transit=1) "if available"; calls must be server-side and comply with branding requirements; unavailable scores must show "Get Score" linking to ws_link. — [Walk Score API docs](https://www.walkscore.com/professional/api.php)
- Pricing: Free tier for showing Walk/Transit/Bike Score for a property; Premium "starting at $115/mo" adds score details, transit data, travel times; Enterprise custom for high-volume, subscription sites, multiple domains or offline use; "Over 5,000 views per day" listed as a paid feature. — [Walk Score pricing](https://www.walkscore.com/professional/pricing.php)
- Third-party R package documentation states the free tier allows 5,000 API calls/day. — [walkscore CRAN README](https://brieger.esalq.usp.br/CRAN/web/packages/walkscore/readme/README.html)

**Numbeo**
- API tiers: Basic USD 260/month (200,000 queries), Professional USD 480/month (1,000,000), Enterprise USD 1,250/month (5,000,000); "Includes commercial usage rights under our Terms of Use"; lookup by city/country or lat/lon; no free trial mentioned. — [Numbeo API](https://www.numbeo.com/common/api.jsp)
- Unofficial Apify scrapers exist (from ~$1.80/1,000 results) but are not sanctioned by Numbeo. — [Apify numbeo-scraper](https://apify.com/solidcode/numbeo-scraper)

**Teleport (cities / quality-of-life API)**
- Directories still list api.teleport.org/api/cities/ with "Quality of Life Data"; no dated source confirms whether the API is live or discontinued in 2024–2026; sources conflict on whether an API key is required. — [publicapis.io](https://publicapis.io/teleport-api); [publicapi.dev](https://publicapi.dev/teleport-api)

**EU "Quality of life in European cities" survey (DG REGIO, 2023 edition)**
- City-level aggregates (revised Sep 2024) and anonymised microdata (SPSS/STATA with codebook), questionnaire and methodology are downloadable; the report states reuse under CC BY 4.0 except third-party elements. — [DG REGIO quality of life page](https://ec.europa.eu/regional_policy/information-sources/maps/quality-of-life_en); [Technical report PDF](https://ec.europa.eu/regional_policy/sources/reports/qol2023/technical_report.pdf)

**OECD Better Life Index / OECD Data Explorer**
- Since 1 July 2024 OECD data, publications and analysis are "freely accessible to everyone, under an open licence"; CC BY 4.0 applies to written content published from that date; Data Explorer covers OECD and selected non-member economies; BLI compares well-being across 11 topics at country level. — [OECD press release, July 2024](https://www.oecd.org/en/about/news/press-releases/2024/07/oecd-data-publications-and-analysis-become-freely-accessible.html); [OECD terms (to verify)](https://www.oecd.org/en/about/terms-conditions.html)

**Copernicus Land Monitoring Service (Urban Atlas, Tree Cover Density, Street Tree Layer, imperviousness)**
- CLMS products are on a principle of "full, open and free access" (Regulation (EU) 1159/2013); users must inform the public of the source, state modifications, not imply EU endorsement; suggested credit: "Generated using European Union's Copernicus Land Monitoring Service information". — [CLMS data policy](https://land.copernicus.eu/en/data-policy)
- Urban Atlas 2021: land cover/land use vector per Functional Urban Area, FlatGeobuf per FUA plus bulk; Urban Atlas 2012 covered 785 FUAs across EEA38 + UK; larger time-series downloads recommended via Copernicus Data Space Ecosystem. — [Urban Atlas 2021](https://land.copernicus.eu/en/products/urban-atlas/urban-atlas-2021); [Copernicus catalogue](https://www.copernicus.eu/en/node/1025)

**Sentinel-2 / NDVI**
- Sentinel data access is "on a free, full and open basis" governed by the "Legal Notice on the use of Copernicus Sentinel Data and Service"; the Data Space Ecosystem imposes account quotas (documented at documentation.dataspace.copernicus.eu/Quotas.html) and bans multiple accounts; other portal content is non-commercial. — [CDSE terms](https://dataspace.copernicus.eu/terms-and-conditions)

**Tree canopy — Global Forest Watch / Hansen UMD**
- GFW data API lists umd_tree_cover_loss as CC BY 4.0, global land (excluding Antarctica/Arctic islands), 30 m, updated annually; cite Hansen et al. 2013. Earth Engine listings of earlier versions also say CC-BY-4.0. — [GFW data API](https://data-api.globalforestwatch.org/dataset/umd_tree_cover_loss); [Earth Engine catalog](https://developers.google.com/earth-engine/datasets/catalog/UMD_hansen_global_forest_change_2018_v1_6)

**Population / census grids**
- Eurostat GISCO Census 2021 grid: EU-wide 1 km² grid (GeoTIFF/GeoPackage/GeoParquet + CSV, EPSG:3035); specific download rules apply to population attributes (TOT_P_2006/2011/2018/2021) with per-country conditions in the metadata PDF; v1.4 (3 Jul 2025) updated 2021 population. — [GISCO population grids](https://ec.europa.eu/eurostat/en/web/gisco/geodata/population-distribution/population-grids); [GISCO grid metadata PDF](https://gisco-services.ec.europa.eu/grid/GISCO_grid_metadata.pdf)
- GHSL (JRC): CC BY 4.0, must cite Pesaresi et al. (2024) IJDE; also mirrored on AWS Open Data (s3://jrc-ghsl). — [GHSL how to cite / use conditions](https://human-settlement.emergency.copernicus.eu/GHSLhowToCite.php); [AWS registry GHS-POP](https://registry.opendata.aws/ghs-pop/)
- INE Portugal: mapas.ine.pt offers Censos 2021 Subsecções Estatísticas, GRID 1000 m × 1000 m, Lugares, Secções, plus "Ficheiro síntese" zips/CSV of variables; the download page shows only an INE copyright notice. INE's general policy (stated in its 2019 publications) is "A informação estatística disponibilizada pelo INE pode ser usada de acordo com a Atribuição 4.0 Internacional (CC BY 4.0)". — [INE mapas download 2021](https://mapas.ine.pt/download/index2021.phtml); [INE ODS 2019 (CC BY wording)](https://ine.pt/ine_novidades/ODS_2019/2); [tesify explainer of BGRI levels](https://tesify.pt/censos-2021-tese-niveis-geograficos-bgri-2026/)
- INSEE France: in 2025 INSEE released census data on 1 km squares and Filosofi (income/social) on 200 m and 1 km squares, with statistical-secrecy suppression; older 200 m grids are mirrored on data.gouv.fr (one derived copy under ODbL). Current licence for Filosofi grids not confirmed (INSEE data is normally Licence Ouverte/Etalab). — [INSEE gridded data](https://www.insee.fr/fr/statistiques/8735103); [data.gouv.fr 200 m](https://www.data.gouv.fr/datasets/donnees-carroyees-a-200m-sur-la-population/informations)
- ONS England & Wales: Output Areas (40–250 households) are the lowest census geography; OA data provided in regional files; ONS content is under Open Government Licence v3.0 except where stated; 2021 OA boundaries and lookups from the Open Geography portal; OA population estimates hosted on Nomis. — [ONS statistical geographies](https://www.ons.gov.uk/methodology/geography/ukgeographies/statisticalgeographies); [UK Data Service OA guide](https://ukdataservice.ac.uk/app/uploads/areaprofilesaccessingdata2023-02-28.pdf)

**Noise — EEA (Environmental Noise Directive)**
- EEA "Data on noise exposure": 2022 round exposure tables (Excel, published 5 Aug 2025) and 2022 noise contours (GeoPackage/GDB/ArcGIS REST/WMS, published 19 Mar 2026); exposure counted in 5 dB bands for Lden (55–59 … >75) and Lnight (50–54 … >70); covers EEA32 + UK. — [EEA noise exposure dataset](https://www.eea.europa.eu/data-and-maps/data/data-on-noise-exposure-7); [EEA quiet areas](https://www.eea.europa.eu/data-and-maps/data/quiet-areas-in-europe-2)
- EEA legal notice: materials published under CC BY 4.0; re-use "for commercial or non-commercial purposes" free of charge with attribution; third-party content and items with their own copyright mark excepted. — [EEA legal notice](https://www.eea.europa.eu/en/legal-notice)

**Air quality**
- EEA Air Quality Download Service: verified (E1a) and up-to-date (E2a) station time series as zipped Parquet "only accessible by scripting or by use of dedicated web-services"; same EEA CC BY 4.0 policy. — [EEA AQ download](https://aqportal.discomap.eea.europa.eu/download-data); [EEA Datahub item](https://www.eea.europa.eu/en/datahub/datahubitem-view/778ef9f5-6293-4846-badd-56a29c70880d)
- OpenAQ: free API key limited to 60 requests/minute and 2,000/hour; one key per person; higher volumes need a paid API License and Services Agreement; OpenAQ only aggregates data "made available for redistribution and use throughout the world" but each source's licence must be honoured and attribution to OpenAQ is required; scraping prohibited; pollutants PM2.5, PM10, SO2, NO2, CO, O3, BC and more. — [OpenAQ rate limits](https://docs.openaq.org/using-the-api/rate-limits); [OpenAQ terms](https://docs.openaq.org/about/terms); [OpenAQ about](https://docs.openaq.org/about/about); third-party aggregator claims a $49 Developer plan — [apispine](https://apispine.com/openaq/pricing) (unverified)

**UN-Habitat / WHO**
- UN-Habitat's Urban Indicators Database (data.unhabitat.org) is the custodian source for SDG 11.7.1; the openly downloadable implementation is the SEDAC 2023 release cited in Q3. — [UN-Habitat 11.7.1 presentation](https://unstats.un.org/sdgs/files/meetings/webex-6sep2018/3. UN-Habitat 11.7.1 Presentation.pdf); [World Bank SDG metadata 11.7.1](https://worldbank.github.io/sdg-metadata/metadata/en/11-7-1)

### Inferences
- A Europe-first product can be built entirely on CC BY / open-government layers with attribution strings; the main licence interaction is ODbL share-alike when OSM-derived metrics are merged into the same published database (keep OSM-derived score layers separable or accept ODbL for the whole output).
- Walk Score is not usable for Portugal/EU at all (US/Canada only), and Numbeo is city-level, survey-based and ≥$260/month, so neither is a good backbone; they are at most comparison points for US/UK users.
- For a Portugal pilot: INE 1 km grid + BGRI subsecção (CC BY 4.0 per INE's general policy, to be confirmed per product), Urban Atlas for Lisbon/Porto/Braga/Coimbra FUAs, EEA noise contours for the agglomerations, Sentinel-2 NDVI for greenness, OpenAQ/EEA stations for air. None of this says anything about running activity; it scores environment and infrastructure.

### Gaps
- Teleport API live/dead status in 2026: unverified.
- Walk Score free-tier daily cap (5,000/day) comes from third-party docs; Walk Score terms page not parsed for caching/display rules.
- OECD: whether CC BY 4.0 explicitly covers Data Explorer datasets (vs written content) not confirmed from the terms page.
- INE: product-level licence for BGRI/grid 2021 not shown on the download page; only INE's general CC BY 4.0 statement found.
- INSEE Filosofi 200 m current licence not confirmed.
- EEA 2022 noise files: licence metadata not read item-by-item (2017 round confirmed under EEA standard re-use policy, with boundaries internal-use only).
- Sentinel Legal Notice PDF could not be text-extracted; exact permitted-use wording not quoted.
- WHO Urban Health Index: no source found.

---

## Key question 5: Mobility data vendors — any free tiers?

### Takeaway
None of the commercial mobility vendors has a self-serve free tier suitable for a public website: Mapbox Movement is sales-only with evaluation samples, StreetLight (now Jacobs) publishes no prices, Replica prices by jurisdiction population for public agencies, Google EIE requires a city-government/NGO sign-up for CSV export. The only free, redistributable mobility-adjacent products are Meta Data for Good's HDX datasets (Movement Distribution Maps, 140+ countries, admin-level, CC BY), which describe how far residents travel, not where they walk or run. Apple and Google COVID mobility reports ended in 2022.

### Cited Findings
- Mapbox Movement: "Access to Mapbox Movement data is restricted to Mapbox customers who have purchased a Mapbox Movement license"; a completed Purchase Contract is required for production data; sample datasets exist for evaluation only; delivery ~2 weeks for US/UK/DE standard products, 3–4 weeks custom. No public price. — [Mapbox Movement overview](https://docs.mapbox.com/data/movement/overview/); [Mapbox Movement guides](https://docs.mapbox.com/data/movement/guides/)
- StreetLight Data: "has not provided pricing information"; now part of Jacobs. — [G2 StreetLight pricing](https://www.g2.com/products/streetlight-data/pricing)
- Replica: pricing for public agencies by tier (city, county, MPO, transit, state) scaled by jurisdiction population, unlimited users per licensed account; no free tier published; regional example — Indianapolis MPO licence open to member-agency email domains only. — [Replica pricing](https://www.replicahq.com/pricing); [Replica help: request access](https://help.replicahq.com/en/articles/6950054-request-data-access-pricing); [Indy MPO](https://indympo.gov/regional-insights/replica/)
- Google Environmental Insights Explorer: transport mode split (walking, cycling, transit, driving) inferred from aggregated Google Maps trips; CSV download requires sign-up as city sustainability professional/government employee (consultants/NGOs working with a city also eligible); older coverage figure: 230 cities public, ~9,616 on request. — [CDP guide to EIE](https://www.cdp.net/en/cities/ghg-emissions-tools-and-datasets-guide-for-cities/google-environmental-insights-explorer); [ICLEI USA](https://icleiusa.org/4-ways-google-eie-transformed-transportation-data-collection/); [EIE resources](https://insights.sustainability.google/resources)
- Meta Data for Good: Movement Distribution Maps show daily share of people travelling 0 km / 0–10 km / 10–100 km / 100 km+ from home, daily observations from Dec 2022, refreshed monthly, "publicly available for 140+ countries on the Humanitarian Data Exchange"; a 2026 peer-reviewed study used them for Türkiye. — [Meta AI for Good: Movement Distribution Maps](https://ai.meta.com/ai-for-good/datasets/movement-distribution-maps/); [ORBi 2026 study](https://orbi.uliege.be/handle/2268/349047); Meta datasets also catalogued on AWS Open Data — [registry.opendata.aws Meta](https://registry.opendata.aws/collab/meta/index.html)
- Apple Mobility Trends discontinued 14 Apr 2022; Google Community Mobility Reports stopped updating after 15 Oct 2022 (archive remains); a 2023 JMIR paper notes Apple, Google and Meta all discontinued these COVID-era services. — [Scientific Reports via DOAJ](https://doaj.org/article/4560ef8c2c484839bd17c5daf705a8fd); [arXiv 2210.09714](https://arxiv.org/abs/2210.09714v1); [JMIR Public Health 2023](https://publichealth.jmir.org/2023/1/e44286)

### Inferences
- Vendor data would only make sense once the site has revenue; indicative entry costs are in the tens of thousands per year for StreetLight/Replica-class products (no vendor publishes a number, so treat as unconfirmed).
- Meta's HDX products are admin-2 level and about trip distance, so they could feed a coarse "how car-dependent is this region" indicator but nothing at neighbourhood scale.

### Gaps
- HDX Movement Range Maps page returned 403; its archived/last-update status and whether Movement Distribution Maps formally replaced it were not confirmed from a primary page.
- No public price for Mapbox Movement, StreetLight or Replica.
- Current (2025–2026) EIE city coverage and whether any EIE data is downloadable without a government account: not confirmed.

---

## Key question 6: Open datasets of actual GPS traces

### Takeaway
The only open, global, ongoing GPS-trace source is OpenStreetMap's uploaded traces, accessible via `/api/0.6/trackpoints` (ODbL, 0.25° bbox, 5,000 points/page, anonymised ordering for older "public" traces) — biased toward mappers and a 2013 bulk dump. Research datasets (GeoLife, FitRec/Endomondo) are non-commercial/academic-only; cities that hold Strava Metro data cannot republish it, and multiple agencies explicitly say so. A public website should not expect to find a redistributable corpus of running/cycling traces.

### Cited Findings
- OSM API `GET /api/0.6/trackpoints?bbox=left,bottom,right,top&page=N`: GPX 1.0 output; max bbox width/height 0.25°; 5,000 points per page; non-trackable traces are returned with waypoints randomised (sorted by lat/lon) as one segment for privacy; trackable traces come first sorted by upload time. As of Aug 2026 the "public" and "private" visibility options are deprecated for new uploads and return an error; only "trackable" and "identifiable" remain. Trace file metadata/downloads are available unauthenticated only if marked public. — [OSM wiki API v0.6](https://wiki.openstreetmap.org/wiki/API_v0.6)
- Visibility semantics: Identifiable = linked to username, listed, timestamps/chronological; Trackable = not linked, not listed, timestamps/chronological; Public (deprecated) = listed, no timestamps, randomised order; Private (deprecated) = not listed, randomised order. "Points are always available via the API" — no level withholds the points themselves. — [OSM wiki: Visibility of GPS traces](https://wiki.openstreetmap.org/wiki/Visibility_of_GPS_traces)
- Bulk dump (planet.gpx): 2,770,233,904 coordinate pairs from OSM's first ~7.5 years, latest version 2013, ~7 GB compressed / 55 GB uncompressed, coordinates only, no track or metadata. — [OSM wiki Planet.gpx](https://wiki.openstreetmap.org/wiki/Planet.gpx)
- Licence of OSM GPS data: 2012 mailing-list thread says the bulk point dumps were CC-BY-SA and API GPX responses were expected to move to ODbL; OSM's current copyright page covers OSM data under ODbL. Community notes: API/JOSM anonymise public traces, and robots.txt disallows /traces/tag/ and /traces/page/ listing paths. — [OSM talk, 2012](https://lists.openstreetmap.org/pipermail/talk/2012-September/064106.html); [OSM help: licence and bulk download](https://help.openstreetmap.org/questions/77300/license-and-bulk-downlad-for-public-tracks/?type=rss); [OSM copyright](https://www.openstreetmap.org/copyright)
- Microsoft GeoLife: 178 users, >4 years (Beijing-centred), 17,621 trajectories, ~1.2 million km; includes hiking and cycling; a SoBigData mirror lists field of use as non-commercial research; Microsoft's download page shows no licence text in search results. — [GeoLife user guide](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/User20Guide-1.2.pdf); [Microsoft download](https://www.microsoft.com/en-us/download/details.aspx?id=52367); [SoBigData mirror](https://ckan-sobigdata.d4science.org/dataset/geolife_-_gps_trajectories_dataset)
- FitRec (UCSD, Endomondo): 253,020 workouts / 1,104 users raw, 167,373 / 956 filtered, with GPS, heart rate, speed, sport type; "for academic use only. Please do not redistribute them or use for commercial purposes." — [FitRec datasets](https://mcauleylab.ucsd.edu/public_datasets/gdrive/fitrec/FitRec-Project.html)
- Strava Metro held by agencies is not republishable: NYSDOT's Strava data "is not publicly accessible and is only available to authorized NYSDOT employees and contractors"; a West Northamptonshire Strava Metro dataset "cannot be shared without written consent from West Northamptonshire Council and Strava"; Bath: Hacked could publish analysis under an open licence but not the data. — [511NY Rideshare](https://511nyrideshare.org/web/analytics-sandbox-for-emerging-mobility-data-sources/strava); [Northampton Pure](https://pure.northampton.ac.uk/en/datasets/strava-metro-data-for-the-baseline-phase-march-2022-of-the-dft-ac/); [Bath: Hacked](https://www.bathhacked.org/projects/bath-cycling/strava-metro-can-tell-us-cycling-bath); University of Glasgow holds anonymised, binned Strava datasets for Glasgow and Tyne and Wear with no open licence shown — [Glasgow research data](https://researchdata.gla.ac.uk/1919/)
- Kaggle: no specific open running/cycling GPS-trace dataset with a clear licence surfaced in searches (see Gaps).

### Inferences
- OSM traces can give a sparse "someone walked/cycled here" prior, especially for trails and parks outside road networks, and they are ODbL-compatible with the rest of an OSM pipeline. But they are tiny next to Strava (billions of points over 20 years, heavily concentrated in Europe) and biased toward mappers, so they are a complement, not a substitute, for a heatmap.
- The research corpora (GeoLife, FitRec) are useful only to prototype algorithms offline; their terms exclude a public commercial site.
- The realistic route to Strava-like data remains: partner with a municipality or university that holds a Metro licence and publish only derived, Strava-reviewed analyses (30-day review clause), or crowdsource consented uploads from the site's own users.

### Gaps
- Current authoritative statement of the licence specifically for OSM GPS traces (vs map data) was not found; sources are 2012–2020 community threads.
- Exact licence text on Microsoft's GeoLife download page not retrieved.
- Kaggle: no dataset verified; any Kaggle GPS-workout upload would carry its own uploader-set licence tag that must be checked individually.
- Whether any city anywhere has published Strava Metro edge counts as open data: none found; searches only turned up explicit refusals.
