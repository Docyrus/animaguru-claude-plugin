# Data contract for an animated chart

Keep enough evidence to reproduce the figure. Use the user's existing data conventions when present; these are the minimum fields to record, not a required file format.

For a spreadsheet (CSV, TSV or Excel), `npm run data -- --animation NAME path/to/file.xlsx` reads every cell into `production/data/NAME.json` by its A1 name, exactly as the file stores it, and prints the first rows to cite. Tie each number the film shows to its cell in `production/facts.json` (the `animaguru-presentation` skill gives the format): `npm run review` then fails a number on screen that no cell supports, and in a presentation it checks every number each slide shows complete. A figure the film works out (a share, a total, a rounded label) cites its source cell, with the calculation in its note.

- Source filename or URL, access date, sheet/table/range, and source hash for local files.
- Row meaning, dimensions, measures, units, date range, timezone and population covered.
- Parsing decisions: decimal separators, currency/percent interpretation, dates, missing values and duplicate rows.
- Filtering, aggregation, conversion, sorting and rounding steps, with original values preserved.
- Chart-ready values keyed by stable series/category IDs; chart domains and display formatting.
- Each numerical claim and its supporting calculation. Identify estimates, uncertainty, projections or illustrative data explicitly.

Validate numerics before rendering. Reject non-finite values. Distinguish zero from absent data. Confirm whether percentages arrive as 0–1 fractions or 0–100 values. Do not add percentages or rates across groups without an appropriate denominator; weighted and unweighted averages answer different questions. Compare dates in a consistent timezone and sort chronologically.

Keep calculations separate from animation interpolation. At each reveal's settled frame, compare the plotted model and displayed label with the expected chart-ready value. Verify totals and rank labels after filtering, and check ties rather than inventing a unique winner. If source and requested claim conflict, describe the discrepancy and use a supported claim or wait for corrected data.

For sensitive source data, the static HTML5 export only needs approved chart-ready values and attribution. Raw source files can stay in `production/`; do not automatically copy them to `public/assets/` or the embedded package.
