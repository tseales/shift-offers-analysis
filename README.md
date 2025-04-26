## Project Overview
The purpose of this analysis was to identify signals in the data which are reflective upon a two-sided marketplace with strong network effects, where workers transact with workplaces to book per diem shifts in the future. The intent being to provide stakeholders with initial insights, recommending directions for further inquiry, with a particular analytical focus on worker and workplace behavior within the product. Conducting an analysis on 266k+ records for 07/2024 &ndash; 01/2025, the insights found and detailed can be found in the following summary. 

*Note:* A PDF copy of the Jupyter Notebook used for EDA can be found [here](https://github.com/tseales/shift-offers-analysis/blob/c35412ab879728e5bad8087706bdc78931c27487/artifacts/shift-offers-notebook.pdf). An ipynb file can be found [here](https://github.com/tseales/shift-offers-analysis/blob/b4658fdecf125e12987e9a53695de9e233f6120f/artifacts/shift-offers-analysis.ipynb) - *images included in its "Summary of Insights" are from local files and will not appear*. This README and aforementioned PDF will reflect all intended charts.

## Summary of Insights

### 1) Created Shifts & Pay Rate
- **Shifts are only created within January, and from July &ndash; December,** with a pause in creation from February &ndash; June. This could be due to missing data, impacting the insights found - it's highly advised to confirm with Data Engineering or applicable stakeholders that there is no unexpected missing data, and what has been collected is accurate.
- **October observes the largest proportion of shifts created,** having ~31% of total shifts created during this time. Historically, July observes a small amount of shifts created (.0011%) with a large spike following from August &ndash; October, before sharply declining in November and having a small rebound into December. This could be due to workplaces accounting for expected increases in patients, due to the proliferation of illness in colder months. Shift deletions and claims follow the same aforementioned pattern.
- **Average MoM pay rate remains relatively steady** as the number of total created shifts fluctuates throughout the year. A sharp increase in creations occur from January &ndash; July due to the apparent pause in created shifts from February &ndash; June. The overall average pay rate is ~\$24.17; July observes the highest average rate, due to the small proportion of shifts posted, at ~\$46.22. This subsequently drops to ~\$24.21 throughout August &ndash; December; however, the pay rate increases on avg. ~\$0.54 throughout this time, with September's increase in shift creations seemingly inducing a ~\$1.08 jump from August.

![created-shifts](https://github.com/user-attachments/assets/312f7a60-38f7-4da2-911b-5cc762e1723b)
</br></br>

### 2) Consistency in MoM Pay Ranges
- **The spread of pay rates is fairly consistent** throughout the year, ranging from \$21-\$26. Notably, although July observes little activity in workplaces creating shifts, the range of pay rates that are posted for this month are about double the usual range. Furthermore, while August comes in second for lowest total shifts created, it experiences a higher standard deviation than other months - meaning pay rates can fall far from its average. 

![pay-rate-box](https://github.com/user-attachments/assets/f49c5648-830f-4497-82d7-4d698de80620)
</br></br>

### 3) Weekly Concentrations - Shift Creations & Claims
- **Monday &ndash; Friday between the hours of 4pm-11pm observe consistently large concentrations of shift creations & claims.** While there are high concentrations found from the hours of 12am-5am, these are all likely due to workers being more active on the platform before, leading up to, and after, a typical workday, likely in preparation for upcoming shifts throughout the current/future weeks. 
    - *Within created shifts:* **Notably, the highest concentration of created shifts occur on Saturdays at 3am.** Mondays at 5pm, Tuesdays at 6pm and 8pm, comprise the top three most common times for creations during the 4pm-11pm timeblock. There is an instance on Thursdays from 8am-10am, where workplaces have high activity. As this is observed to be a typical downtime, understanding if this activity is contributed by a specific workplace, or subset, will help aid in knowing the likely reason(s) for such a deviation and if more attention to this case is warranted/needed. 
    - *Within claimed shifts:* **Mondays at 8pm comprise the highest concentration for shift claims,** with other claims during the 4pm-11pm timeblock being relatively consistently high. This general pattern seems to track with the flow of the workplace-worker relation in the product, having high-concentrations of created shifts being followed by high concentrations of claimed shifts. Tuesdays at 12am comprise the 2nd highest concentration for claimed shifts, following the observed pattern of worker-activity outside of the typical workday hours. Similarly to the high amount of shifts typically created at 3am on Saturday, claims observe a high period of activity from 3-5am, albeit not its most observed for a specific timeblock. 
- **Throughout the whole week, 6am-1pm has relatively low periods of shift creations & claims**.

![shift-concentrations](https://github.com/user-attachments/assets/40276f41-d793-4084-846b-3d311bdf3935)
</br></br>

### 4) Workplace Shift Deletions
- **No workplace deletes more shifts than they create.**
- **~21% of all shifts are deleted,** with ~.07% of these shifts having already been claimed by a worker. Depending on the deletion tolerance of stakeholders, understanding what contributes to a worker deleting a shift can provide direction on product adjustments that may lower the total percentage of shifts being deleted.
- **5% of workplaces nearly delete shifts as much as they create,** one workplace in particular deleting 99.7% of their created shifts, others deleting above 50%. 

![table-deletion-ratio](https://github.com/user-attachments/assets/e2e3b10f-f5da-4101-a52a-3f1602177d55)
</br></br>

### 5) Recommendations
1. **Investigate the large spike of shift creations during the winter months, October in particular.**
    - This may be due to the expectation of a rise in illness during the colder months of the year, as is typically observed of society. Workplaces may be attempting to account for an influx of patients during peak periods.
    - Further corroborating theory on the large spike can potentially provide new avenues for accommodating any flexibility needed in the platform for workplaces, when trying to balance predictions of peak periods and their resulting realities.
2. **Further investigate concentrations of shift creations.**
    - Understanding if specific concentrations are attributed to a select number of workplaces will aid in knowing which workplaces may be highly influential in the data being shown. This is especially true for any concentrations observed which do not follow general patterns - e.g., Thursdays from 8-10am, and Saturdays at 3am for shift creations.
    - Further context will aid in understanding of the contributing factors to a shift being created during certain hours, and can possibly aid in a paired-supplementation of understanding the deletions of shifts observed. 
3. **Understand what contributes to ostensible anomalies in July & August.**
    - With July having such little shifts created and no deletions, but with higher pay rates, it'd prove useful to know what's contributing to this deviation - is it a specific workplace; are there factors about the shifts that contribute to higher rates; do these factors not occur often and is why there is a low amount of these high rate shifts being created? This understanding can be paired with further contextual data on why workplaces decide to post a shift with a certain rate, creating a potential avenue for product improvement by accommodating for the needs of these "unique" shifts.
    - With August following July in the lowest number of shifts created, understanding why it has a higher standard deviation than months with greater number of shifts created can provide a more detailed insight into factors that contribute to pay rate decisions. This would aid in workplace relations by creating a better understanding of shift use-cases/scenarios and continue further informing potential product improvement opportunities. 
3. **Collate qualitative data to understand what factors contribute to a workplace deleting a shift.**
    - While workplaces may be overestimating their workforce needs for peak periods, causing shifts to be subsequently deleted once posted, there may also be mistakes made when a shift is posted which aren't able to be corrected without deleting the shift.
    - Understanding why workplaces delete shifts can potentially provide insight(s) that allows for platform adjustments to be made, decreasing the overall percentage of shifts deleted, and increasing the opportunities available for workers.
