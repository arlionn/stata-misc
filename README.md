# Miscellaneous Stata commands

Production-ready commands:

- `doa`: "abbreviated do". Instead of typing `do 1_import_data` you can type `doa 1` (as long as it's unambiguous)
- `mise_en_place`: create the folder structure for a new project
- `kosi`: shorthand for `keep order sort isid` ([details here](kosi.md))
- `hshell`: hidden shell, so you can run shell commands on Windows without the annoying popups (requires the `parallel` package)
- `mata_filefilter`: alternative to filefilter implemented in Mata. Started as a workaround to an odd bug in filefilter, but might be extended further
- `bitfield`: niche program; if you have data by i,j (for `#j` small), you sometimes want to collapse by `i` and add variables `has_j` for each level of `j`. This does so in a memory-efficient way, by compressing the dummies into ["bitfields"](https://en.wikipedia.org/wiki/Bit_field)
- `pick_ticks`: alternative rule for selecting ticks for a plot axis

Beta commands:

- `fast_destring`: faster alternative to destring. Works well but only a few options and might change.

Experimental commands:

- `block`: experiment on how to use the undocumented `_request2` option
- `parallel_map`: (undocumented) distribute tasks on multiple instances of Stata; based on -parallel-


## Installation

```stata
loc packages doa mise_en_place kosi hshell mata_filefilter bitfield pick_ticks fast_destring parallel_map
loc location "https://github.com/sergiocorreia/stata-misc/raw/master/src"

foreach package of local packages {
	cap ado uninstall `package'
	net install `package', from(`location')
}
```


## Local installation


```stata
loc packages doa mise_en_place kosi hshell mata_filefilter bitfield pick_ticks fast_destring parallel_map
loc location "C:\Git\stata-misc\src"

foreach package of local packages {
	cap ado uninstall `package'
	net install `package', from(`location')
}
```

## Extra install do-files

- [install_all.do](install_all.do)
- The [dependencies](https://github.com/sergiocorreia/stata-misc/tree/master/dependencies) is useful if you are behind a firewall that blocks https but allows `wget` (as some network Linux servers do).

