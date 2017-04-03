# Before 1.3

## Performance
- Parallelize read dropout computation
  - Make functions and call them with parallel
  - or launch in background and `wait` to summarize

## Feature
- Report real number of reads (not unique reads) affected by multiple hits
  - Python script
- Make `bold.fasta.gz` available online

## Benchmarking
- Victoria's dataset first 100k sequences per sample

## Documentation
- Describe input sequence format requirements
  - file name
  - fastq and/or fastq.gz
- Describe test dataset on `github.com/enormandeau/barque_test_dataset`
  - Include good `primers.csv` file

## Finish paper
- Finish first draft
- Add references

-----------------------------------------------------------------------------

# Later

## Database formatting
- Revise bold formating scripts
  - Correctness
  - Possible to retain more sequences?
  - Shortest sequences at ~300bp. Too short?

## Features
- R script to produce read dropout figure and run from `01_scripts/08_...sh`
- Report barcode splitting results for each sample
- Support single-end data (no merge -> pseudo-merge script)
- Support interleaved input (flash can treat it)

## Performance
- Have 2 values for the number of CPUs:
  - For data preparation steps (read-write intensive)
  - For the vsearch steps (computation intensive)
- Blast only unique sequences for the whole dataset (v2.0)
  (big boost if lots of samples)
  - Create dictionary of unique reads
  - Blast them and store results
  - Assign results to each read of each pop