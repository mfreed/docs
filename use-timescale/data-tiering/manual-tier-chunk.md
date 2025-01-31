---
title: Manually Tier data
excerpt: How to manually tier Timescale data
product: [ cloud ]
keywords: [ data tiering, tiering ]
tags: [ storage, data management ]
---

# Manually tiering chunks

Once Data Tiering has been enabled on a service individual chunks from a Hypertable may be tiered to object storage.

Before you start, you need a list of chunks to tier. In this example, you use a hypertable called example, and tier chunks older than three days.

<Procedure>

### Selecting chunks to tier

1. At the psql prompt, select all chunks in the table `example` that are older
   than three days:

   ```sql
   SELECT show_chunks('example', older_than => INTERVAL '3 days');
   ```

1. This returns a list of chunks. Take a note of the chunk names:

   ```sql
   ||show_chunks|
   |---|---|
   |1|_timescaledb_internal_hyper_1_2_chunk|
   |2|_timescaledb_internal_hyper_1_3_chunk|
   ```

</Procedure>


When you are happy with the list of chunks, you can use the `tier_chunk` function to manually tier each one.

<Procedure>

### Tiering chunks manually

1. At the psql prompt, tier the chunk:

   ```sql
   SELECT tier_chunk( '_timescaledb_internal_hyper_1_2_chunk');
   ```
   
   Tiering a chunk is an asynchronous process that schedules the chunk to be tiered.

1. Repeat for all chunks you want to tier.

</Procedure>


## List tiered chunks

<Highlight type="info">
Tiering a chunk schedules the chunk for migration to object storage but, won't be tiered immediately. 
It may take some time tiering to complete. You can continue to query a chunk during migration.
</Highlight>

To see which chunks are tiered into object storage, use the `tiered_chunks`
informational view:

```sql
SELECT * FROM timescaledb_osm.tiered_chunks;
```

If you need to untier your data, see the
[manually untier data][untier-data] section.

## Creating a tiering policy

Most users don't need to manually tier chunks and instead create a [data tiering policy][creating-data-tiering-policy] to automate when chunks are tiered. 


[creating-data-tiering-policy]: /use-timescale/:currentVersion:/data-tiering/creating-data-tiering-policy/
[untier-data]: /use-timescale/:currentVersion:/data-tiering/untier-data/
