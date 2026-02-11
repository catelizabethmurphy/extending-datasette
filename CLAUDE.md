# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Datasette project for exploring and extending Datasette's features, including geocoding, mapping, and full-text search. The project uses Datasette plugins and command-line tools to work with CSV data loaded into SQLite databases.

## Setup and Dependencies

Install required Python packages:
```bash
pip install sqlite_utils datasette geocode-sqlite
```

Install Datasette plugins:
```bash
datasette install datasette-codespaces
datasette install datasette-cluster-map
datasette install datasette-configure-fts
```

## Common Commands

### Starting Datasette
```bash
datasette serve extend.db
```
Serves the database on a local web server for browsing and querying data.

### Loading CSV Data
```bash
sqlite-utils insert extend.db <table_name> data/<filename>.csv --csv
```
Examples:
- `sqlite-utils insert extend.db refunds data/refunds.csv --csv`
- `sqlite-utils insert extend.db admissions data/admissions.csv --csv`
- `sqlite-utils insert extend.db releases data/releases.csv --csv`

### Geocoding Addresses
```bash
geocode-sqlite nominatim extend.db <table_name> \
  --location="{address_one}, {city}, {state} {zip}" \
  --delay=1 \
  --user-agent="newsapps-<your-name>"
```
Uses OpenStreetMap's Nominatim geocoder to add latitude/longitude columns to tables with address data. The `--delay=1` parameter adds a 1-second delay between requests to respect rate limits.

## Data Structure

The project includes three CSV datasets in the `data/` directory:

**refunds.csv**: ~1,000 political contribution refund records from Maryland
- Contains address fields: address_one, city, state, zip
- Intended for geocoding demonstration

**admissions.csv**: School admissions data with existing lat/lon coordinates
- Already has latitude and longitude fields for mapping
- Includes school names, acceptance rates, locations

**releases.csv**: Congressional press releases
- Contains title and body text fields
- Used for full-text search demonstrations

## Datasette Features

### Cluster Map Plugin
The datasette-cluster-map plugin automatically displays map visualizations for tables with latitude and longitude columns. After geocoding the refunds table or viewing the admissions table, maps will appear automatically.

### Full-Text Search
Configure full-text search via the web UI at `/-/configure-fts/extend`. Select which table columns should be searchable (typically title and body fields for the releases table), then use the search interface to query across those fields.

### Faceting
Datasette's faceting feature allows filtering and grouping data by column values. Click on column headers in the web interface to add facets and explore data patterns.

## Database

- **extend.db**: Main SQLite database file
- Tables are created via sqlite-utils when loading CSV files
- Geocoding adds `latitude` and `longitude` columns to tables
