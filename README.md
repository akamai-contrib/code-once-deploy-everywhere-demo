# code-once-deploy-everywhere-demo
Sample repo from Edge World breakout session

## Creating Pipeline Folder Structure

```
akamai pipeline new-pipeline -p astronaut-training -e prp_XXXXX dev stage prod -g grp_XXXXX --variable-mode user-var-value
```

This command creates the pipeline (folder) name and structure.  It takes the source property id and creates the specified environment folders, which then can be checked into a repository.


## Adding/Modifying/Simplifying Environments

Simplify envInfo.json to just have the name (see example in each one inside the environments folder)
Simplify projectInfo.json to just have the environment names list and pipeline name (see example)

To add a new environment, add the desired new folder in the environments folder and add the envInfo.json and the new variables.json values for that environment. Update projectInfo.json, and the variables.json accordingly.


## Merge

```
akamai pipeline merge -n -p astronaut-training dev
akamai pipeline merge -n -p astronaut-training stage
akamai pipeline merge -n -p astronaut-training prod
```

This command does the find/search of all the variables defined in the variableDefinitions.json, environments folder variables.json file, and the rule /template .json files.  Arrays and objects are also able to be substituted as well. The merge output will go in the /dist folder and will be the full raw artifact that can be used to update the desired configuration.  The -n argument (no-validate) is importannt so that it only does the merge (find/replace) locally.  Run this command from one directory above.
