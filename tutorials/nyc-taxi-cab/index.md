---
title: Query time-series data tutorial
excerpt: Learn how to query time-series data
products: [cloud, mst, self_hosted]
keywords: [tutorials, query, learn]
tags: [tutorials, beginner]
layout_components: [next_prev_large]
content_group: Analyze NYC taxi cab data
---

import PreloadedData from "versionContent/_partials/_preloaded-data.mdx";

# Analyze NYC taxi cab data

New York City is home to about 9 million people. This tutorial uses historical
data from New York's yellow taxi network, provided by the New York City Taxi and
Limousine Commission [NYC TLC][nyc-tlc]. The NYC TLC tracks over 200,000
vehicles making about 1 million trips each day. Because nearly all of this data
is time-series data, proper analysis requires a purpose-built time-series
database, like Timescale.

## Prerequisites

Before you begin, make sure you have:

*   Signed up for a [free Timescale account][cloud-install].

## Steps in this tutorial

This tutorial covers:

1.  [Setting up your dataset][dataset-nyc]: Set up and connect to a Timescale
    service, and load data into your database using `psql`.
1.  [Querying your dataset][query-nyc]: Analyze a dataset containing NYC taxi
    trip data using Timescale and PostgreSQL.

## About querying data with Timescale

This tutorial uses the [NYC taxi data][nyc-tlc] to show you how to construct
queries for time-series data. The analysis you do in this tutorial is similar to
the kind of analysis data science organizations use to do things like plan
upgrades, set budgets, and allocate resources.

It starts by teaching you how to set up and connect to a Timescale database,
create tables, and load data into the tables using `psql`.

You then learn how to conduct analysis and monitoring on your dataset. It walks
you through using PostgreSQL queries to obtain information, including how to use
JOINs to combine your time-series data with relational or business data.

<PreloadedData />

[dataset-nyc]: /tutorials/:currentVersion:/nyc-taxi-cab/dataset-nyc/
[query-nyc]: /tutorials/:currentVersion:/nyc-taxi-cab/query-nyc/
[advanced-nyc]: /tutorials/:currentVersion:/nyc-taxi-cab/advanced-nyc/
[nyc-tlc]: https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page
[cloud-install]: /getting-started/:currentVersion:/#create-your-timescale-account
