# kinship-matrix
 code is present in kinship-matrix.R

 example file name is same-allele.xlsx


library(readxl)

library(gplots)

library(ggplot2)

library(viridis)

# upload identical varieties data in excel
kinship_data <- read_excel("~/Desktop/allele_matching/kinship_matrix/same.xlsx", sheet = "Sheet1", col_names = TRUE)

View(kinship_data)

