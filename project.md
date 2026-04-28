import seaborn as sns
import matplotlib.pyplot as plt
from data_utils import select, convert_columns_to_int

sns.set_theme()

analysis_data = select(
    combined,
    ["pre_lecture_videos", "difficulty", "pace", "understanding", "would_recommend"]
)

analysis_data_int = convert_columns_to_int(
    analysis_data,
    ["pre_lecture_videos", "difficulty", "pace", "understanding", "would_recommend"]
)

chart1 = sns.displot(
    data=analysis_data_int,
    x="pre_lecture_videos",
    bins=7
)
chart1.set(title="Student Support for Optional Pre-Lecture Videos")
chart1.savefig("chart1.png")

chart2 = sns.catplot(
    data=analysis_data_int,
    kind="bar",
    x="difficulty",
    y="pre_lecture_videos"
)
chart2.set(title="Support for Pre-Lecture Videos by Course Difficulty")
chart2.savefig("chart2.png")

chart3 = sns.relplot(
    data=analysis_data_int,
    kind="scatter",
    x="understanding",
    y="pre_lecture_videos",
    hue="would_recommend"
)
chart3.set(title="Understanding Compared with Support for Pre-Lecture Videos")
chart3.savefig("chart3.png")

## Results

Students generally supported optional pre-lecture videos. Students who wanted more preparation resources often reported that videos would help their learning experience.

## Conclusion

Based on the survey data, optional pre-lecture videos appear to be a useful improvement for COMP 110.

They are low-risk because they are optional, but they may improve preparation and understanding.

A future step would be testing the videos for several weeks and comparing quiz scores, attendance, and student feedback.