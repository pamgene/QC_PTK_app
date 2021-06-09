# PTK_Kinetic_QC_app

##### Description

`PTK_Kinetic_QC_app` is an application that will perform a linear regression on each kinetic curve in the data set and calculate the probability p that there is no trend with cycle number (time).  If this p-value is low it means that there likely is a trend with cycle number.
Such a trend can be positive or negative, therefore the app calculates a "presence" value as the -log10(p) times the sign of the slope of the linear regression:
`presence = -log10(p) * sign(slope)`
Hence a presence value > +2 indicates a positive trend observed at a significance < 0.01.

In addition to returning the presence value for each kinetic it will return the fraction of arrays with a positive trend for each peptide (presence > 2) as a spot annotation: ...fractionPresent. This value maybe used to e.g. exclude peptides from further analysis for which a positive trend is observed in only a minor fraction of the samples.

##### Details

Use the kinetics of your PTK measurement to select well expressed peptides for further by selecting peptides that show a positive trend during the incubation. Each kinetic curve receives a score that can be used to determine if a clear positive trend is present. In addition it calculates for each peptide in what percentage of the samples or arrays measured such a clear positive trend is observed. Visualizations of the results are implemented to assist the user in selecting well expressed peptides for further analysis.
The application consists of a data input, a workflow and a data output. 

The input data is the [ptk dataset](https://tercen.com/r/35c33fa33c9e6aba0dce6483f5f70135)

This workflow has 4 operators:
- [identity_operator](https://github.com/tercen/identity_operator)
- [presence_operator](https://github.com/tercen/minus_operator)
- [merge_operator](https://github.com/tercen/merge_operator)

This workflow has 2 views:
- Kinetics colored by presence
- Presence Map

##### See Also

[PTK_Kinetic_QC_app](https://github.com/tercen/PTK_Kinetic_QC_app)
