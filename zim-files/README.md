## Zim Files Readme

This directory must exist if you will use the Kiwix-serve container.

***IMPORTANT***: The `kiwix-serve` container will not run without any `.zim` files stored in the `./zim-files/` directory. At least one `.zim` file must exist in the `./zim-files/` directory.

Content can be downloaded from the [Kiwix library](https://library.kiwix.org/) (URL: https://library.kiwix.org/), as a `.zim` file then loaded into the Kiwix server.  If you are using `wget` or automation, use the [download.kiwix.org/zim](https://download.kiwix.org/zim/) site.


## Examples to get and pull files

### Getting the file list with PowerShell

Here is an example to get the list of files from the [https://download.kiwix.org/zim/other/](https://download.kiwix.org/zim/other/) page, using PowerShell:
```
$URL="https://download.kiwix.org/zim/other/"
$urlObject=Invoke-WebRequest -URI $URL -UseBasicParsing
$urlOuterHTML=$urlObject.Links.OuterHTML
$fileList=$urlOuterHTML | % {$_.Split('"')[1]} | Select-String -NoEmphasis -Pattern "\.zim"
```

You can then further filter the list for English only files:
```
$fileList | Select-String -NoEmphasis -Pattern "_en_"
```

You can also use regex to filter through the files with the regex `(\S+)(_\d{4}-\d{2}\.zim$)` ([here on regex101](https://regex101.com/r/a3yplk/1)):
```
$fileList | % {[regex]::Match($_, '(\S+)(_\d{4}-\d{2}\.zim$)').Groups[1].Value} | Get-Unique
```

#### Getting a list of English zim files

You can combine the examples above to get a list of English zim files, using PowerShell:
```
$fileList | Select-String -NoEmphasis -Pattern "_en_" | % {[regex]::Match($_, '(\S+)(_\d{4}-\d{2}\.zim$)').Groups[1].Value} | Get-Unique
```

### Examples using `wget` to pull files

Here are some examples using the `wget` command to pull files from [https://download.kiwix.org/zim/](https://download.kiwix.org/zim/):
```
wget https://download.kiwix.org/zim/other/zimgit-water_en_2022-03.zim
wget https://download.kiwix.org/zim/zimit/rapsberry_pi_docs_2023-01.zim
wget https://download.kiwix.org/zim/wikipedia/wikipedia_en_for_schools_maxi_2023-02.zim
wget https://download.kiwix.org/zim/other/artofproblemsolving_en_all_maxi_2021-03.zim
wget https://download.kiwix.org/zim/stack_exchange/cooking.stackexchange.com_en_all_2022-11.zim
wget https://download.kiwix.org/zim/zimit/fas-military-medicine_en_2022-05.zim
wget https://download.kiwix.org/zim/other/zimgit-medicine_en_2022-03.zim
wget https://download.kiwix.org/zim/ted/ted_en_playlist-before-public-speaking_2021-01.zim
wget https://download.kiwix.org/zim/ted/ted_en_playlist-things-to-do-to-make-steam-lea_2022-08.zim
wget https://download.kiwix.org/zim/stack_exchange/gardening.stackexchange.com_en_all_2022-11.zim
```
