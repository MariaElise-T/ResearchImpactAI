# Research Impact AI

## Training Data

Publish or Perish (PoP) was used to sample 1000 papers per year from 2000 to 2024 from Crossref for a total of 25000.  Papers were included if and only if they had at least one author affiliated with Texas State University.  Publish or Perish data features metadata including DOI, title, author list, year published, journal or conference title, abstract, citation count, and bibliographic information.  

The PoP data was augmented using PlumX Metrics and Altmetrics - two databases that collect alternative metrics on academic literature including main stream media mentions, social media mentions, patent citations, policy citations, download counts, and reader counts.  By incorporating alterative metrics, a more robust training set is constructed that allows the model to consider a wider scope of factors when evaluating the impact of an academic work.
### Data collection and cleaning 
- **Altmetric_API_pull.ipynb** - Pulls data from the Altmetrics API using the DOIs collected by PoP and saves the output to *altmetric_data.json*.
- **PlumMetric_API_pull.ipynb** - Pulls data from the PlumX API using the DOIs collected by PoP and saves the data to *plumx_metrics_data.json*.
- **plummetrics_altmetrics_tabular.ipynb** - Converts json formatted data to tabular format and eliminates entries that cause parsing errors. It takes *altmetric_data.json* and *plumx_metrics_data.json* as input and produces *altmetrics_tabular_uncleaned.csv* and *plumx_metrics_tabular_uncleaned.csv*.
- **plumx_altmetrics_cleanup.ipynb** - Drops unneeded or duplicate columns, drop duplicate rows based on DOI (first observance kept), and replaces unknown values with 0.  Takes *altmetrics_tabular_uncleaned.csv* and *plumx_metrics_tabular_uncleaned.csv* as input and produces *plumx_metrics_tabular_cleaned.csv* and *altmetrics_tabular_cleaned.csv*.
- **crossref_altmetric_plumx_merge.ipynb** - Merges all crossref years into one dataframe, replaces missing crossref values with 0, and pulls journal impact factors when available.  Also merges crossref, plumx, and altmetrics sources.  Takes *altmetrics_tabular_cleaned.csv*, *plumx_metrics_tabular_cleaned.csv*, and *TXST_crossref_XXXX.csv* as input and produces *crossref_allyears.csv* and *allsources_merge.csv*.

## Model Development



## Model Testing

## Model Inference

## Future Maintenance


