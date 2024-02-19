# kinship-matrix
 code is present in kinship-matrix.R
 example file name is same-allele.xlsx
library(readxl)
install.packages("gplots")
library(gplots)
library(ggplot2)
library(viridis)

# upload identical varieties data in excel
kinship_data <- read_excel("~/same.xlsx", sheet = "Sheet1", col_names = TRUE)
View(kinship_data)

# upload data for heatmap
variety_names <- kinship_data$varieties
numeric_data <- kinship_data[, -1]

# Create a heatmap using heatmap.2 with sample names on the y-axis
heatmap.2(as.matrix(numeric_data),
          col = colorRampPalette(c("red", "green"))(10),
          main = "identical varieties",
          xlab = "Varieties",
          ylab = "Samples",
          trace = "none",
          margins = c(28, 26),
          Rowv = FALSE,          # Display hierarchical clustering on rows
          Colv = FALSE,         # Do not display hierarchical clustering on columns
          labRow = variety_names  # Display variety names on the y-axis
)


# option2 is good to differtiate all the differences among the varieries especially after 90%
custom_colors <- c(colorRampPalette(c("#FF0000", "#FF4500", "#FE632A", "#E8A317", "#FFD700"))(80),
                   colorRampPalette(c("#FFD700", "#00FF00"))(10),
                   colorRampPalette(c("#00FF00", "#008000"))(10))

heatmap.2(as.matrix(numeric_data),
          col = custom_colors,
          main = "Identical Varieties",
          xlab = "Varieties",
          ylab = "Samples",
          trace = "none",
          margins = c(28, 26),
          Rowv = FALSE,         # Do not display hierarchical clustering on rows
          Colv = FALSE,         # Do not display hierarchical clustering on columns
          labRow = variety_names  # Display variety names on the y-axis
)

# different color pallets for color blind people following the option2
custom_colors <- viridis(100)

heatmap.2(as.matrix(numeric_data),
          col = custom_colors,
          main = "Identical Varieties",
          xlab = "Varieties",
          ylab = "Samples",
          trace = "none",
          margins = c(28, 26),
          Rowv = FALSE,         # Do not display hierarchical clustering on rows
          Colv = FALSE,         # Do not display hierarchical clustering on columns
          labRow = variety_names  # Display variety names on the y-axis
)





