# Create the environment to replicate code in Random Genes paper
The paper [Association between expression of random gene sets and survival is evident in multiple cancer types and may be explained by sub-classification](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1006026)
describes an analysis where random sets of genes are tested for their association with survival in cancer datasets.
This dockerfile creates an Rstudio environment with the required packages installed and with the code downloaded. 

To build the image run
``` bash
docker build -t random_genes_rstudio .
```

Then, to start the container run 
``` bash
docker run --rm -ti -e PASSWORD=yourpassword -p 8787:8787 random_genes_rstudio
```
where it is of course advisable to change the text `yourpassword` to your preferred password.

This will open an Rstudio service that can be accessed through localhost:8787.
When requested enter the username `rstudio` and the password you chose above. 
Then you can run the code as described in [the code github](https://github.com/yishaishimoni/Random_Genes).
