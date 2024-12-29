
```{r}
#Setting the WD folder in RStudio
setwd("/Users/douglasmesadrigewehr/Desktop/WD RStudio")

#The following R code creates a new object with the name of your choice (in this example I am using 'ma', containing all the outcomes in a data frame object.

sheet_names <- excel_sheets("data2.xlsx") 

ma <- lapply(sheet_names, function(x) {
  as.data.frame(read_excel("data2.xlsx", sheet = x)) } )

names(ma) <- sheet_names

sheet_names
```


```{r}
#Performing the binary outcome data meta-analysis

m.acm <- metabin(event.e, n.e, event.c, n.c,
                 data = ma$acm,
                 method = "MH",
                 method.tau = "DL",
                 sm = "RR",
                 studlab = Author)
```

