---
title: "Mengambil Tweet Berdasarkan Keyword"
author: "Cici Mulyani"
output: html_document
---

```{r}
# Install library (Cukup Sekali Saja)
install.packages("rtweet")
```

```{r}
# Load library
library(rtweet)
```

```{r}
# Set Token
token <- create_token(
  app = "novasi-1",
consumer_key = “fbqT0mBw9ehG9IhmT2XTSb0Ti”,
consumer_secret =”MJaEGWTR396VqFWZQDmnybqGwbvydCTFFJ9KFLtsMH7vMgfmkr”,
access_token = “1323866871288877057-mhauIZAemtLfS4gPxWlyPe6EyGuszv”,
access_secret = “fDGMlo6xREFKr4gs3qD6GgoetdFeiFz1DdwuKPJHSsaDL”
)
```

```{r}
# Tentukan Kata Kunci, Jumlah Tweet, dan Bahasa
keyword <- "omicron"
jumlahtweet <- 500
bahasa <- "id"
retweet <- TRUE
```

```{r}
# Proses Pengumpulan Data Tweet 
tweet_keyword <- search_tweets(keyword,
  n = jumlahtweet,
  include_rts = retweet,
  type = "recent",
  lang = bahasa,
  retryonratelimit = FALSE
)
```

```{r}
# Simpan data tweet dengan format .csv
write_as_csv(tweet_keyword,
  "data/tweet-keyword.csv",
  prepend_ids = TRUE,
  na = "",
  fileEncoding = "UTF-8"
)
```
