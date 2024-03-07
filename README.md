# PTK_QC_app

`PTK_QC_app` is used to determine whether peptide signals show a positive trend during the incubation. Each kinetic curve receives a presence score that can be used to determine if a clear positive trend is present.

### Details 

`PTK_QC_app` performs a linear regression on each kinetic curve in the data set and calculates the probability p that there is no trend with cycle number (time).  If this p-value is low, it means that there likely is a trend with cycle number.
Such a trend can be positive or negative, therefore the app calculates a "presence" value as the -log10(p) times the sign of the slope of the linear regression:
`presence = -log10(p) * sign(slope)`
Hence a presence value > +2 indicates a positive trend observed at a significance < 0.01.

In addition to the presence value for each kinetic curve, it returns the fraction of arrays with a positive trend for each peptide (presence > 2) as a row factor (spot annotation): .fractionPresent. This value is used to exclude peptides from further analysis for which a positive trend is observed in only a minor fraction of the samples. As default, peptides with positive trend in less than 25% of samples are exluded.

Visualizations of the results are implemented to assist the user in selecting well expressed peptides for further analysis.

This workflow has 2 operators:

* [identity_operator](https://github.com/tercen/identity_operator)
* [PTK_QC_presence_operator](https://github.com/tercen/PTK_QC_presence_operator)

This workflow has 2 views:

* Kinetics colored by presence
* Presence Map