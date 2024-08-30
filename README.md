


![StataMin](https://img.shields.io/badge/stata-2015-blue) ![issues](https://img.shields.io/github/issues/asjadnaqvi/stata-ternary) ![license](https://img.shields.io/github/license/asjadnaqvi/stata-ternary) ![Stars](https://img.shields.io/github/stars/asjadnaqvi/stata-ternary) ![version](https://img.shields.io/github/v/release/asjadnaqvi/stata-ternary) ![release](https://img.shields.io/github/release-date/asjadnaqvi/stata-ternary)


---

[Installation](#Installation) | [Syntax](#Syntax) | [Examples](#Examples) | [Feedback](#Feedback) | [Change log](#Change-log)

---

![ternary_banner](https://github.com/user-attachments/assets/1c0d3590-2469-41b0-88f4-6d8099fb8f75)



# ternary v1.0
(28 Aug 2024)

This package provides the ability to draw ternarys Stata.


## Installation

The package can be installed via SSC or GitHub. The GitHub version, *might* be more recent due to bug fixes, feature updates etc, and *may* contain syntax improvements and changes in *default* values. See version numbers below. Eventually the GitHub version is published on SSC.

The SSC version (**v1.0**):

```stata
ssc install ternary, replace
```

Or it can be installed from GitHub (**v1.0**):

```stata
net install ternary, from("https://raw.githubusercontent.com/asjadnaqvi/stata-ternary/main/installation/") replace
```

The `palettes` package is required to run this command:

```stata
ssc install palettes, replace
ssc install colrspace, replace
```

Even if you have the package installed, make sure that it is updated `ado update, update`.

If you want to make a clean figure, then it is advisable to load a clean scheme. These are several available and I personally use the following:

```stata
ssc install schemepack, replace
set scheme white_tableau  
```

You can also push the scheme directly into the graph using the `scheme(schemename)` option. See the help file for details or the example below.

I also prefer narrow fonts in figures with long labels. You can change this as follows:

```stata
graph set window fontface "Arial Narrow"
```


## Syntax

The syntax for the latest version is as follows:

```stata
        ternary varL varR varB [if] [in], [ cuts(num) zoom fill points lines labels colorL(str) colorR(str) colorB(str) lwidth(str) msymbol(str) msize(str) mcolor(str) mlcolor(str) mlwidth(str) labcolor(str) ticksize(str) *  ]
```

See the help file `help ternary` for details.

The most basic use is as follows:

```
ternary varL varR varB
```

representing left, right and bottom variables respectively.


## Citation guidelines
Software packages take countless hours of programming, testing, and bug fixing. If you use this package, then a citation would be highly appreciated. Suggested citations:


*in BibTeX*

```
@software{ternary,
   author = {Naqvi, Asjad},
   title = {Stata package ``ternary''},
   url = {https://github.com/asjadnaqvi/stata-ternary},
   version = {1.0},
   date = {2024-08-28}
}
```

*or simple text*

```
Naqvi, A. (2024). Stata package "ternary" version 1.0. Release date 28 August 2024. https://github.com/asjadnaqvi/stata-ternary.
```


*or see [SSC citation](XXXX) (updated once a new version is submitted)*




## Examples

Set up the data:

```stata
use "https://github.com/asjadnaqvi/stata-ternary/blob/main/data/NUTS3_pop.dta?raw=true", clear

lab var y15prop "Age 0-14"
lab var y64prop "Age 15-64"
lab var y99prop "Age 65+"
```

Test a basic figure

```
ternary y15prop y64prop y99prop 
```

<img src="/figures/ternary1.png" width="100%">


Re arrange the variables:

```
ternary y64prop y99prop y15prop
```

<img src="/figures/ternary2.png" width="100%">


Test `ternary` with fractions:

```stata
gen double y15prop2 = y15prop / 100
gen double y64prop2 = y64prop / 100
gen double y99prop2 = y99prop / 100


ternary y64prop2 y99prop2 y15prop2
```

<img src="/figures/ternary2_1.png" width="100%">

### Colors


```
ternary y64prop y99prop y15prop, fill
```

<img src="/figures/ternary3.png" width="100%">


```
ternary y64prop y99prop y15prop, fill lcolor(black)
```

<img src="/figures/ternary4.png" width="100%">


### Cuts

```
ternary y64prop y99prop y15prop, fill cuts(3)
```

<img src="/figures/ternary5.png" width="100%">


```
ternary y64prop y99prop y15prop, fill cuts(10)
```

<img src="/figures/ternary6.png" width="100%">

```
ternary y64prop y99prop y15prop, fill cuts(6)
```

<img src="/figures/ternary7.png" width="100%">


```
ternary y64prop y99prop y15prop, fill cuts(6) zoom
```

<img src="/figures/ternary7_1.png" width="100%">

```
ternary y64prop y99prop y15prop, fill cuts(6) zoom msize(2.5) mc(black%60)
```

<img src="/figures/ternary7_2.png" width="100%">

```
ternary y64prop y99prop y15prop, fill cuts(8) zoom msize(2.5) mc(black%70) lw(0.08) labcolor(gs6)
```

<img src="/figures/ternary7_banner.png" width="100%">


### Additional options

```
ternary y64prop y99prop y15prop, fill zoom cuts(6) ///
	colorB(lime) 
```

<img src="/figures/ternary8.png" width="100%">


```
ternary y64prop y99prop y15prop, fill zoom cuts(6) ///
	colorB(red) colorL(green) colorR(blue)
```

<img src="/figures/ternary9.png" width="100%">

```
ternary y64prop y99prop y15prop, fill zoom cuts(4) ///
	colorB(red) colorL(green) colorR(blue) mcolor(white%60) mlc(black) msize(3)	
```

<img src="/figures/ternary10.png" width="100%">

### other color palettes

```
ternary y64prop y99prop y15prop, points zoom cuts(6)
```

<img src="/figures/ternary11.png" width="100%">

```
ternary y64prop y99prop y15prop, fill points zoom cuts(6)
```

<img src="/figures/ternary12.png" width="100%">

```
ternary y64prop y99prop y15prop, points zoom cuts(6) lw(0.05) msize(2.5)
```

<img src="/figures/ternary13.png" width="100%">


```
ternary y64prop y99prop y15prop, lines labels zoom cuts(6) msize(2.5) points malpha(60)
```

<img src="/figures/ternary14.png" width="100%">

```
ternary y64prop y99prop y15prop, lines labels zoom cuts(6) msize(2.5) 
```

<img src="/figures/ternary15.png" width="100%">


```
ternary y64prop y99prop y15prop, lines labels zoom cuts(6) msize(2.5) mlc(black) mc(white%60)
```

<img src="/figures/ternary16.png" width="100%">

```
ternary y64prop y99prop y15prop, lines labels zoom cuts(6) msize(2.5) mlc(black) mc(white%70) lw(0.3) msym(triangle)
```

<img src="/figures/ternary17.png" width="100%">



## Feedback

Please open an [issue](https://github.com/asjadnaqvi/stata-ternary/issues) to report errors, feature enhancements, and/or other requests. 


## Change log

**v1.0 (28 Aug 2024)**
- First release.





