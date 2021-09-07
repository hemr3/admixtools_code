library(admixtools)
library(tidyverse)

prefix = "~/analyses/snp_to_vcfs/admixtools/high_cov/highcov_LDinvariate_pruned"
  #directory structure; contains .bed, .bim., .bam, and .fam files
  
my_f2_dir = "~/analyses/snp_to_vcfs/f2_data/"
    
extract_f2(prefix, my_f2_dir, overwrite = T)
    
f2_blocks = f2_from_precomp("~/analyses/snp_to_vcfs/f2_data/")

for (i in 3){ 
    numadmix <- i
  
  opt_results = find_graphs(f2_blocks,
                            outpop = "African",
#                            numrep = 25,
                            numgraphs = 200,
#                            numgen = 200, #
#                            numsel = 4,
                            numadmix = numadmix,
#                            opt_worst_residual = TRUE,
                            keep = "best",
                            stop_gen = 1500
)
winner <-  opt_results %>% top_n(1, -jitter(score))
graph_winner <- plot_graph(winner$edges[[1]])
}
  #running admixtools algorithm; setting number of migrations to be chosen each run. 
  #checking the top score and z-score of the best-fitting graph
  
  # plotting and saving the winner graph
graph_winner <- plot_graph(winner$edges[[1]])
ggsave(graph_winner, file = paste0("~/Pictures/Visualisations/admixtools/aug_graphs/afr_outgroup_highcov_adm1"), 
       device = "png", width = 5, height = 5)
        
