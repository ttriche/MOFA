# Basic MOFAmodel object
MOFAmodel it is the main S4 class used to store all relevant data to analyse a MOFA model. Its slots are the following (accessible using @):
* **InputData**: input data, either a list of matrices or a MultiAssayExperiment
* **TrainData**: training data, a list of matrices with processed data (centered, scaled, etc.)
* **TrainOpts**: training options
* **DataOpts**: data processing options
* **ModelOpts**: model options
* **TrainStats**: training statistics
* **Expectations**: random variables' expectations
* **Parameters**: random variables' parameters

# List of relevant functions

## Prepare and run MOFA
* **createMOFAobject**: first function to create an untrained MOFA model from input multi-omics data  
* **prepareMOFA**: prepare an untrained MOFA, always run it after createMOFAobject and before runMOFA  
* **runMOFA**: function to train an untrained MOFA model. This calls the Python framework  
* **loadModel**: load a trained MOFA model  

## get functions
* **factorNames**: get or set factor names  
* **featureNames**: get or set feature names  
* **sampleNames**: get or set sample names  
* **viewNames**: get or set view names  
* **getDimensions**: get dimensions (number of samples, features, etc.)  
* **getFactors**: get model factors  
* **getWeights**: get model weights  
* **getTrainData**: get training data  
* **getImputedData**: get imputed data  

## Disentangle sources of variation
* **calculateVarianceExplained**: calculate variance explained by each factor in each view. This is the key plot of MOFA and should always be done before inspecting factors or weights. It can retrieve either the fraction of total variation (totalVar=T) or the fraction of residual variation (totalVar=F), use both options.  

## Inspect loadings
* **plotTopWeights**: plot the top loadings for a given factor and view  
* **plotWeights**: plot all loadings for a given factor and view  

## Inspect factors
* **FactorsCorPlot**: correlation plot between factors. Ideally, they should be uncorrelated  
* **FactorsScatterPlot**: scatterplot between two factors, this is similar to doing a PCA plot  
* **FactorsScatterPairs**: pairwise combination of scatterplots between multiple factors  
* **FactorBeeswarmPlot**: beeswarm plot for a single factor  

## Inspect training data
* **showDataHeatmap**: heatmap of the training data using only top features for a given factor. This is very useful to map the factors and features back to the original data  
* **showDataScatter**: scatterplot of the data using only top features for a given factor  

## Feature set enrichment analysis
* **FeatureSetEnrichmentAnalysis**: do feature set enrichment analysis. Takes a bit amount of options, check the example on the vignette  
* **LinePlot_FeatureSetEnrichmentAnalysis**: plot the top most enriched feature sets per factor  

## Clustering
* **clusterSamples**: k-means clustering of samples on the latent space (similar to what iCluster does)  

## Compare models
* **compareModels**: compare factors and weights between multiple runs of the model  

## Impute missing values
* **imputeMissing**: impute missing data  




