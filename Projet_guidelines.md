# Schedule
The schedule for the projects is as follows:

* Milestone P1, due 23:59 CET, 08 Oct 2021 (10% of the project): To be done individually, where each student submits an outline of project ideas of up to 500 words by filling a Google Form.
* Milestone P2, due 23:59 CET, 12 Nov 2021 (20% of the project): To be done as a team, where the team submits a GitHub repository that includes: (1) a well-organized README containing the detailed project proposal (up to 1000 words), and a notebook containing initial analyses and data handling pipelines. We will grade the correctness, quality of code, and quality of textual descriptions.
* Milestone P3, due 23:59 CET, 17 Dec 2021 (70% of the project): To be done as a team, where the team submits a data story using a platform of their choice, and the project GitHub repository containing your final notebook. We will grade the correctness, quality of code, and quality of textual descriptions.

The bulk of your work should be over before Christmas, in order for you to focus on the exam (and exams of other classes).
Note: Additional details about each project milestone are available below.

## P1: First glimpse at the data
For Milestone 1, each team member will, individually, perform the following tasks:

1) Read the paper about the Quotebank dataset that will be used for the projects. You can find the paper here. If you don’t fully grasp the technical details about the machine learning methods, that’s totally fine. What matters is that you understand what the Quotebank dataset is and from what kind of source data it was derived.

2) Familiarize yourself with the Quotebank dataset.
   * We have prepared for you a sample (available via Google Drive) of the dataset that contains quotes from The New York Times from 2019. Please explore this sample, and familiarize yourself with the dataset. The best way to do this is by playing around with it, for example, by extracting summary statistics and reading samples of quotes. For the rest of the project you will be able to work with data for all the years (2015-2020), but for the Milestone 1 you are only required to work with 2019.
   * In case you are curious, the entire dataset is available here. The data that we provide support with is the “Quotation-centric version”. Note that there is no need to load and analyze the entire dataset for Milestone 1.
   * Optionally, here is a website that you can use to visually explore the dataset. Note that this website is experimental (and not required for your projects), so we can’t guarantee that it will function seamlessly (but we think it will come in handy!). In case you encounter any issues, please report them in this Zulip stream.
3) Once you have explored the sample, propose at least three bold and creative ideas for proposals of projects that could be done with the Quotebank dataset. At this stage, it does not matter whether the ideas are feasible or not. The ideas proposed in Milestone 1 will not necessarily turn out to be the project you will eventually do. The idea of this first milestone is to get the juices flowing, get you in a creative mode, and at the same time get your hands dirty!
**P1 deliverable**: An outline of project ideas of up to 500 words (done individually). The outline of project ideas is submitted by filling a Google Form. Note that for this first milestone we are not going to grade any code.

## P2: Project proposal and initial analyses
When you are done with Homework 1, you will continue to work on the next project milestone. In Milestone 2, together with your team members, you will agree on, and refine, your project proposal. Your first task is to select a project. Even though we provide the main dataset for you to use, it is your responsibility to check that what you propose is feasible given the data (including any additional data you might bring in yourself), and to perform initial analyses.

Note that we will support you in working with Quotebank data from 2015 to 2020, inclusive. You are, of course, free to use the data from other years if you wish so, but only if you are feeling adventurous! We have also prepared for you a Google Colab notebook with code to get you started with loading the dataset.

The goal of this milestone is to intimately acquaint yourself with the data, preprocess it and complete all the necessary descriptive statistics tasks. We expect you to have a pipeline in place, fully documented in a notebook, and show us that you have clear project goals.

When describing the relevant aspects of Quotebank data, and any other datasets you may intend to use, you should in particular show (non-exhaustive list):
* That you can handle the data in its size.
* That you understand what’s in the data (formats, distributions, missing values, correlations, etc.).
* That you considered ways to enrich, filter, transform the data according to your needs.
* That you have a reasonable plan and ideas for methods you’re going to use, giving their essential mathematical details in the notebook.
* That your plan for analysis and communication is reasonable and sound, potentially discussing alternatives to your choices that you considered but dropped.

We will evaluate this milestone according to how well these steps have been done and documented, the quality of the code and its documentation, the feasibility and critical awareness of the project. We will also evaluate this milestone according to how clear, reasonable and well thought-through the project idea is. Please use the second milestone to really check with us that everything is in order with your project (idea, feasibility, etc.) before you advance too much with the final Milestone 3! There will be project office hours dedicated to helping you.

You will work in your project GitHub repository that will be created by using the link we provide. Follow this link to create your public repository dedicated to the project.

The repository will automatically be named ada-2021-project-<your_team_name>. By the Milestone 2 deadline, each team should have a single public GitHub repo under the epfl-ada GitHub organization, containing the project proposal and initial analysis code.

**External sources for enriching Quotebank data**: To help you on your Quotebank ADAventure, we would like to provide you access to additional metadata about the speakers in the Quotebank dataset. This information is available for ~9M unique Wikidata entities (identified with their QIDs) as a .parquet file named speaker_attributes.parquet via Google Drive. Note that the schema of speaker_attributes.parquet is also available within the same Google Drive folder that hosts the parquet file. You can load this file as a pandas dataframe using df = pd.read_parquet(<path_to_file>). Pandas requires pyarrow to read parquet files, which can be installed using conda install pyarrow -c conda-forge.

Additionally, we also provide you with sample code (available in the same Google Drive folder) along with instructions on how to execute it, which was used to extract the aforementioned information about speakers from the Wikidata knowledge base. You are free to extend the provided code to extract additional information about speakers than what is already provided by us. Please be advised that the Wikidata dumps (you need to use the wikidata-<timestamp>-all.json.gz file) are usually very large (~100GB) in size, so don’t leave it until the last minute to parse/extract information from this resource. For additional information about Wikidata dumps and how to download them, please see this Wiki page.

P2 deliverable (done as a team): GitHub repository with the following:

* README.md file containing the detailed project proposal (up to 1000 words). Your README.md should contain:
  * Title
  * Abstract: A 150 word description of the project idea and goals. What’s the motivation behind your project? What story would you like to tell, and why?
  * Research Questions: A list of research questions you would like to address during the project.
  * Proposed additional datasets (if any): List the additional dataset(s) you want to use (if any), and some ideas on how you expect to get, manage, process, and enrich it/them. Show us that you’ve read the docs and some examples, and that you have a clear idea on what to expect. Discuss data size and format if relevant. It is your responsibility to check that what you propose is feasible.
  * Methods
  * Proposed timeline
  * Organization within the team: A list of internal milestones up until project Milestone 3.
  * Questions for TAs (optional): Add here any questions you have for us related to the proposed project.
* Notebook containing initial analyses and data handling pipelines. We will grade the correctness, quality of code, and quality of textual descriptions.

## P3: Final project and the datastory
When you are done with Homework 2, in Milestone 3, you will execute the project you proposed. For the final milestone, you will be expected to execute your project proposal, and describe your project in a data story.

Data stories are a blog post or short article, with an important visual component, using data to tell a story and illustrate it effectively. You can be less formal here (although methods and math should then appear in the notebook), but more visual. You can pick your preferred platform option, but we encourage you to use Jekyll. We prepared a short tutorial for creating a website with github pages outlining how you can host the datastory. You submit the story by providing a URL to it in your README file.

A (single!) supporting notebook extending the one delivered for Milestone 2 is also expected and will be graded. The README in Milestone 3 shall be updated. It should also detail the contributions of all group members.

There will be project office hours dedicated to helping you finish the project successfully. The bulk of your work will be over before the winter break, so you can focus on the exam (and exams of other classes) during that time.

*Example*
* John: Plotting graphs during data analysis, crawling the data, preliminary data analysis;
* Mary: Problem formulation, coming up with the algorithm;
* Chris: Coding up the algorithm, running tests, tabulating final results;
* Eve: Writing up the report or the data story, preparing the final presentation.

### P3 deliverables (done as a team):

1) The final project repository containing your final notebook. We will grade the correctness, quality of code, and quality of textual descriptions.
2) Data story


## Bonus: Quotebank issue reporting
We encourage you to report any data issues you encounter throughout the course of your Quotebank ADAventure using this Google form. A few sample issues already identified by the ADA teaching staff are available in this Google sheet for your reference. Your inputs will not only help improve the Quotebank data to the benefit of the scientific community, but also fetch you some bonus points for your project. The teams with the most useful reports will be awarded an up-to-10% bonus for the project grade.