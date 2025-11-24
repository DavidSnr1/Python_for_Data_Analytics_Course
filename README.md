# The Analysis
## 1. What are the most demanded skills for the top 3 most popular data roles?
To find the most demanded skills for the 3 most popular data roles, I first filtered out the 3 data roles with the most job postings. Then I plotted them with their required skills. Each value shows the likelyhood of a skill being required for the respective job.

View my notebook with detailed steps:
[Skill_Demand.ipynb](Python_for_Data_Analytics_Course\03_Project_Section\Skill_Demand.ipynb)

### Visualize Data
```
fig, ax = plt.subplots(len(job_titles), 1)

for i, job_title in enumerate(job_titles):
    df_plot = df_skill_perc[df_skill_perc['job_title_short'] == job_title].head()
    sns.barplot(data=df_plot, x='skill_perc',  y='job_skills', ax=ax[i], hue='skill_count', palette='crest')
    ax[i].set_ylabel("")
    ax[i].set_xlabel("")
    ax[i].legend().set_visible(False)
    ax[i].set_xlim(0,70)
    ax[i].set_title(job_title)
    for j, v in enumerate(df_plot['skill_perc']):
        ax[i].text(v+1, j, f'{v:.0f}%', va='center')

    if i != len(job_titles)-1:
        ax[i].set_xticks([])


fig.suptitle("Likelyhood of Job Skills in Postings", fontsize=15)
fig.tight_layout()
```
### Results
![Required skills for top 3 most popular job](images\top_skills_of_most_popular_jobs.png)

