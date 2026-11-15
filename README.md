# grasshopper-documentation
📚 Documentation of IfcHopper (formerly IfcHopperShell), the Grasshopper plugin for openBIM.

The website is live at
https://ifchopper.github.io/grasshopper-documentation/

- `docs/` is the current version (v1.0-beta); `versioned_docs/version-0.1/` is IfcHopperShell 0.1.
- `docs/components/` is generated from the plugin (`tools/SampleBuilder --docs` in the [code repository](https://github.com/IfcHopper/grasshopper-code)); do not edit it by hand.
- Build locally with `npm ci` and `npm run build`; pushing to `main` deploys the site.

## Beta.2 build validation (2026-11-13)

`npm ci` and the production build passed with Node 22.16.0 / npm 10.9.2. The built sample ZIP was hash-checked against the candidate files. npm reported 66 dependency vulnerabilities (9 low, 15 moderate, 24 high, 18 critical). This is an unresolved documentation dependency audit finding; dependencies were not upgraded as part of the release. The deployed output is a static site. The build also warned about stale browser-support metadata.

## Beta.3 build validation (2026-11-15)

Regenerated 62 component pages from the extracted beta.3 Release ZIP and refreshed the sample download with all 17 examples (36 files, each SHA-256 checked against source). The production build passed using the existing installed dependencies and local Node/npm tools. Updated installation, migration guidance and version labels for Rhino 8/.NET 8 and Rhino 9/.NET 10. The initial restricted Node build stalled; the rerun outside the sandbox passed. The build warned about stale browser and baseline metadata. The beta.2 dependency audit finding above remains unresolved; no new dependency audit or upgrade was performed. No deployment was performed.
