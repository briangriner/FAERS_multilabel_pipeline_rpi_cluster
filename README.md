# FAERS_multilabel_pipeline_rpi_cluster
Example notebook with a pipeline for multilabel classifier using dask distributed on a 4 node raspberry pi cluster. I built the cluster using 3 4GB 4B pis, 1 8GB pi and an inexpensive unmanaged network switch. Setup used ssh with static ips and sshfs for a mount point on the scheduler node. Dask distributed works beautifully in this environment and is very simple to use. Some algs in sklearn didn't work for the multilabel wrapper like random forrest and mlp classiers but the other classiers that supported multilabel worked fine. Dask also has a bokeh dashboard for the scheduler that is very helpful in debugging. NOTE: THIS IS A DEVELOPMENT ENVIRONMENT AND NOT RECOMMENDED FOR PRODUCTION USE.

Quick note on the FAERS safety data and why I used the multilabel classifier. Data is grouped by quarter but not aggregated at the case level (i.e. each case can have multiple outcomes on separate rows). My analysis is at the patient level so I flatted the outcome table so that each row is a case and different outcomes are in different columns. Since each patient can have multiple outcomes, multilabel made the most sense to use. 

Here is a link to the FAERS quarterly data. https://fis.fda.gov/extensions/FPD-QDE-FAERS/FPD-QDE-FAERS.html I only used the outcome and demo tables for this example. There are more tables linked to specific drugs that could be usesful as well.
