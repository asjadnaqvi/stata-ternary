


![StataMin](https://img.shields.io/badge/stata-2015-blue) ![issues](https://img.shields.io/github/issues/asjadnaqvi/stata-ternary) ![license](https://img.shields.io/github/license/asjadnaqvi/stata-ternary) ![Stars](https://img.shields.io/github/stars/asjadnaqvi/stata-ternary) ![version](https://img.shields.io/github/v/release/asjadnaqvi/stata-ternary) ![release](https://img.shields.io/github/release-date/asjadnaqvi/stata-ternary)


---

[Installation](#Installation) | [Syntax](#Syntax) | [Examples](#Examples) | [Feedback](#Feedback) | [Change log](#Change-log)

---

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

```

See the help file `help ternary` for details.

The most basic use is as follows:

```
ternary numvar, by(variable(s))
```


where `numvar` is a numeric variable, and `by()` is upto three string variables, ordered by higher aggregated levels to finer units. The algorithm changes the layout based on `xsize()` and `ysize()`. See examples below.



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

```



## Feedback

Please open an [issue](https://github.com/asjadnaqvi/stata-ternary/issues) to report errors, feature enhancements, and/or other requests. 


## Change log



**v1.0 (28 Aug 2024)**
- First release.





