clootl_data = list()

fullTree2021 <- treeGet("1.3","2021", data_path="~/projects/otapi/AvesData") 
fullTree2022 <- treeGet("1.3","2022", data_path="~/projects/otapi/AvesData") 
fullTree2023 <- treeGet("1.3","2023", data_path="~/projects/otapi/AvesData")
clootl_data$trees$`Aves_1.3`$summary.trees$year2021 <- fullTree2021
clootl_data$trees$`Aves_1.3`$summary.trees$year2022 <- fullTree2022
clootl_data$trees$`Aves_1.3`$summary.trees$year2023 <- fullTree2023


tax2021 <- taxonomyGet(2021, data_path="~/projects/otapi/AvesData")
tax2022 <- taxonomyGet(2022, data_path="~/projects/otapi/AvesData")
tax2023 <- taxonomyGet(2023, data_path="~/projects/otapi/AvesData")

clootl_data$taxonomy.files$Year2021 <- tax2021
clootl_data$taxonomy.files$Year2022 <- tax2022
clootl_data$taxonomy.files$Year2023 <- tax2023

annot_filename <- "~/projects/otapi/AvesData/Tree_versions/Aves_1.3/OpenTreeSynth/annotated_supertree/annotations.json"
all_nodes <- jsonlite:::fromJSON(txt=annot_filename)

clootl_data$trees$`Aves_1.3`$annotations <- all_nodes
save(clootl_data, file="~/projects/otapi/clootl/data/clootl_data.rda")