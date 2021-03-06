<h1 align="center" style="font-weight: bold !important">โก๏ธ๐ Boostagram Files</h1>

<p align="center">
  Filter and split JSON Lines output from `lntlvs.sh` into individual files. Only TLVs matching a specified filter will be put into files.
</p>

<h3 align="center">
  <a href="#-examples-">Examples</a>
  <span> ยท </span>
  <a href="#-usage">Usage</a>
</h3>

## ๐ซ Examples

By default the script only outputs TLVs containing a `"message"`  of at least length one. This is intended to filter out Podcast Metadata TLVs (key `7629169`) which contain a boostagram message.

### 1๏ธโฃ File Input

๐ Run:

``` shell
./split.sh custom_records.jsonl custom_records/
```

๐จ This will write files to `custom_records/`

``` shell
custom_records
โโโ custom_record_00000.json
โโโ custom_record_00001.json
(...)
โโโ custom_record_NNNNN.json
```

### 2๏ธโฃ Standard Input

You can also pipe JSON Lines directly to the script by specifying `-` as input file:

๐ Run:

``` shell
./lntlvs.sh --jsonlines | ./split.sh - custom_records/
```

๐จ This will, again, write files to `custom_records/`

``` shell
custom_records
โโโ custom_record_00000.json
โโโ custom_record_00001.json
(...)
โโโ custom_record_NNNNN.json
```

## ๐ Usage

```
Usage:
    ./split.sh [OPTIONS] INPUT_FILE OUTPUT_DIR

    Writes each line in INPUT_FILE to a file in OUTPUT_DIR.
    The filenames will be 'custom_record_NNNNN.json' where 'NNNNN' is an incrementing number starting with '00000'.
    If INPUT_FILE is set to '-', the script will read from stdin.

Options:
    --filter <value>    Outputs only those lines matching the given filter (case-insensitive). (default: \"message\":\".+\")
