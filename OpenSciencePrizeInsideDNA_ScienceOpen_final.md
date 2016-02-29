Introduction and statement of need
----------------------------------

Research reproducibility is one of the most pressing issues in the fields of
life science and biomedical research [1]. Arguably, 35 to 50% of studies in life
science are either difficult to replicate or do not confirm original findings
[2]. Exponential growth of generated data and consequently poor and inefficient
data re-use are among the top causes of reproducibility crisis. While the “human
factor” partly plays a role in limited data re-use, major hurdles are still
cased by technological challenges. We identify three primary technical
challenges that limit efficient data re-use: (1) the need for scalable computing
to process public datasets, (2) detachment of code and data repositories from a
computing environment, and (3) detachment of data, code, and computing
environment from an article publication process.

Powerful computing is often required for processing of open data.
Conventionally, scientific data processing is tackled with dedicated servers
and/or computer clusters. However, this approach has multiple drawbacks in the
era of open data. First, only \~5-10% of universities have core cluster
facilities [3]. Second, biology and life science researchers are often
unqualified for IT administration and face difficulties maintaining dedicated
lab servers. Third, unlike in physics or mathematics, most software in life
science is MPI-incompatible [4], thus requiring individual computer nodes being
high in RAM and CPU - a condition rarely met in clusters and servers. Finally,
neither clusters or servers allow any efficient way of data and code sharing
because of security policies of the universities and cluster/server physical
isolation. These issues make dependence on HPC/servers one of the blocking
factors for efficient data re-use.

The second contributor to limited data re-use is a separate hosting of
computational tools (software and code), data repositories and computing
environments. Such separation implies that to re-use open data, researchers need
to download datasets, find and install computational tools and set up a
computational environment. Online transfer of large data severely impedes
re-use: for example, in bioinformatics, complete ENCODE dataset needs \~40Tb of
space [6], which makes it difficult to download and arrange sufficient storage
space on a server or even a cluster. Inefficient code sharing is an additional
blocking barrier [5]. We analysed \>25000 research papers published in last 20
years in the field of bioinformatics and found that over 85% of researchers
publish their code in a self-hosted manner [4]. This results in a weak
maintenance and quickly outdating code which is hard to discover and apply to
open data. Therefore, separation of code, data and computation make data re-use
very time and effort consuming.

Third factor is a complete detachment of article publication process from an
environment that would allow other researchers to reproduce analysis and re-use
the data and code. At most, publishing platforms (i.e. journals) allows to
include a link to an external website with a raw data and code. However,
research reproducibility depends on ability of others to repeat all steps in an
article “methods” section. For that, not only original data, links to the tools
and computing environment need to present, but also a set of software settings
used to analyse a particular dataset. Such settings are most often buried among
lines of text in supplementary materials, impossible to access for automated
machine processing and hard to find for end users. We collectively call this
problem an effective “settings” sharing and re-use. Ideally, data, code,
settings should be stored as an executable bundle, embedded into the articles
and shared during an article publication process.

  
In conclusion, an unprecedented data growth in life science hampers research
reproducibility and presents challenges to open science. Traditional approaches
with research articles, code, data and methods being decoupled from each other
and stored in hardly accessible formats on isolated clusters and servers
profoundly limit re-use of all four components.

 

Goal
----

In our proposal, we present two platforms - InsideDNA (EU side) and ScienceOpen
(US side) and explain how the development of these platforms and their
integration can boost efficient data, code and settings/method re-use and
increase research reproducibility in general.

 

Method
------

### InsideDNA - UK collaborator

InsideDNA is a cloud-based platform for open science and reproducible research
in life and biomedical science. The platform is tailored for bioinformatics and
genomics, but based on user feedback is now expanding to other areas of life
science. It is comprised of three components: research platform, tool publishing
service and sharing service.

*Research platform*

To facilitate re-use of code and provide access to powerful computational
resources, we developed InsideDNA research platform. It is a unified web
interface to hundreds of open source bioinformatics tools. These tools can be
instantly executed on a user dataset or downloaded as Docker containers (Fig.
1). Users can monitor progress of submitted analysis tasks and easily see when
and why tasks fail or succeed (Fig. 2). Each user has its own storage space
which grows as more data are added and can hold terabytes of data. There are
almost no limits on data storage size [8], number of compute nodes and their
RAM/CPU capacity, because InsideDNA is based on a Google cloud technology and is
autoscaled.

Figure 1. Access, search and download of open source tools

![](<https://lh4.googleusercontent.com/FmvcJbXw_2k_Lq0VsrnZ5_8bSrItmbSDxoL6qRq3a9jlqfKbzOh2ysO03z9y3JYEjeGOnfCjUds4d_PnCJKmmITQvf4OB9_SZPkPPvko5iN28Dkqoxzw-DP5E2CENFSDr4Offk6n>)

Figure 2. Tasks monitoring

![](<https://lh5.googleusercontent.com/yCeZz_rz_2RxpEC-xzhJycVCQY_nv6U4F6plDiKrHp7iXf_oho8bZcE29M35rLcjqqo-60AW5G1c8MjGYfPvRdFYhQpxkqKXVfxQz5KPUqa9jO-VHAT_s-0kUmvQlfzGkPaRMkmk>)

To promote data re-use in life science, we developed an intuitive web file
manager (Fig. 3). Web-based file manager is an interface to a cloud-based user
storage containers and it supports all conventional operation on datafiles (Fig.
3). Importantly, file manager will be able to access external data source (e.g.
S3, Dropbox, Drive) or database (e.g. NCBI, dbSNP, FlyBase) via so-called
interoperability connector. Files and dataset from these external sources are
visualized in the file manager and can be explored by an end user. In one click,
user can run analysis on external data or copy external datasets to his own
storage container. Interoperability connector is essential for public data
re-use, because it has scalable architecture and allows to connect new open data
sources as they become available for public.   

Figure 3. Web-based file manager

![](<https://lh4.googleusercontent.com/T62hN0Q9W1vivdPsNoZzQcrgyR36Zh2gd_GNrKJ_9UxQkA3ueCFPvdHbfbwx77kMbtHTLnv0kXoMCH0F_mNUc4JO4uz5kJy8tZQPu0qsPsgSrVr9X7PjpZwkxUn8WU6y3sz60dNt>)

  
To equip researchers with an analysis framework, we developed a web interface
for tool/software execution. This interface has default and advanced modes.
Default mode is an easy-to-use web interface to all tools (Fig. 4), whereas
advanced mode is a conventional console-based access to all tools and cloud task
submission (Fig. 5). Console looks just like UNIX terminal, but has a completely
different architecture: each submitted task initiates a launch of an execute
node from the Google cloud, therefore offering enormous flexibility on a number
of concurrently submitted tasks and node capacity. In addition to execution of
individual tools, users can interactively chain tools together and create custom
sharable bioinformatics pipelines.

Figure 4 Default mode - form-based interface

![](<https://lh4.googleusercontent.com/0ZP7r7u1c7gHvHyGv08KgSp8r7TZfgdSseO_fYqFmnO-XR0mepukYPGlAAEWB_i6w35vRTdrp8gs-02Jk2yVqVNsC6vFIVrgzJvhRgAFMn0Ze7zQ2WibItGIXSSevFkQhgXxTIea>)

Figure 5. Advanced mode - console access

![](<https://lh5.googleusercontent.com/ZGuh2lt5e8WI2hYybeuduLCYhifVROrCVKxNYX8WhkryyB5tTP43O1FAbU-ZEDwAEjlCXfJtQ_XZNXksQAOTWUjKQYXNxuwwXNpRxrPhXhHujsjabTthr3zld4VLcdUkODnFAoy8>)

To promote international and between-team collaboration regardless of user
affiliation and location, we encourage users to work in teams. To facilitate
teamwork, users are able to organise tasks, datasets, tools into sharable
projects (Fig. 6). By participating in a shared project, all project members
gain access to the same datasets, are able to monitor tasks submitted by project
members, share tools and tool settings. Project-based approach is available with
both default and console-based interfaces.

Figure 6. Sharable projects with tools, tasks, and data

![](<https://lh3.googleusercontent.com/zdYCr-3L9cMHMr9izaPyKNoDjpJy7QQjrINuIWVRiXVR35TjKPWsh5EEHG541kKMsPB2rCc6hLwqYN0BTX7sf09NY6MhxnZSRXhyeVIgUIhv9qG2N0G7V0rUOa-T4ebUFTn-xtEo>)

*Tool publishing service*

To foster code/software re-use, we are developing a tool publishing service - a
web service for tool publishing. Tool author only needs to provide a link to
code repository with a source code (e.g. github) or source code itself, tool
description, any particular installation instruction and a test dataset via an
easy web form (Fig. 7). Then tool is automatically compiled and run on a test
dataset. The output is then verified by the tool author. If approved, the tool
becomes publically available in three formats - default, console and
downloadable Docker container.

Figure 7. Tool publishing interface

![](<https://lh4.googleusercontent.com/6xMirUo0O5JLlDh4lAZfXUPeEmpMBm_6f2oVCNx2PpVzadvHBPv1nBAWITJC2EPb1551fOrHVJDc8jE0sd9p1ZRRO5b4R3UcYJxUhD0Tobbuw49noz7AucP1YDg8Stas9pFwvIgx>)

*Sharing service*

To make all analysis reproducible in life science, we are developing a sharing
service - a way to store and share direct web urls to tool, data, and tool
settings as an executable bundle which we call iMethod (Fig. 8). These web urls
allow to quickly access and re-run an entire method section from a research
article. Urls can be shared as permanent links, mainly serving a journal article
publication purpose; and temporally (e.g. 2 weeks expiration time) - for sharing
analysis between peers (Fig. 9). Importantly, if iMethod is shared publicly,
associated datasets get transferred to public storage containers, url gets DOI
and become indexed (Fig. 10-12) by major search engines (e.g. Google, Yahoo,
Bing). Each link is annotated by
[codeMeta](<https://github.com/codemeta/codemeta>) schema [8], and thus is
perfectly compliant with the state-of-art progress on discoverability of
scientific software in the Web.  

Figure 8. Example of iMethod ready to be saved as a link

![](<https://lh4.googleusercontent.com/uoxnqZgxdozXIOsy6RJb1z6xSClkHNK-weT5RTG8e204ms4mOA66ro5POmqgoRsEhDQIECzfDWkQO9JNsB4JvnSOHC8-fKywdOFPRZRSUO3BX0CsGnRrMlF-qh3uq6yGkW4V16h2>)

Figure 9.1. Link creation: associated datasets get transferred to a public
storage

![](<https://lh5.googleusercontent.com/FE61hBSL-X7G7FL2bIs1QqoHCrDmBVOXH4MyEJzfJnwsCe08kDqKJxJ15ljNA5XqfahckV4vgDp2ysQR5UO29c_ybf9JeRHqfYdjQxjuFDfrGtZcWMuLgulfmoBnzYKNTTCF3gEt>)

Figure 9.2. Link creation - url for sharing

![](<https://lh5.googleusercontent.com/r0xQnW8P7ExIVlEAELLfnfU925mCKtujIhR8-50JHmj16lEncVHQaiNVEUrgoq3NPVayFLrkNgWsRlpMrWf-wgGYlcGm4ymerfB8Z7voxh2L55rtcV1tyWuZ9Tp9U_vjU2Uy8QS9>)

Figure 10. Link indexing and visualization in Google scholar search results

![SearchResultsInsideDNA (1).png](<https://lh6.googleusercontent.com/hHnVWmNO4QU-gW5zb-vFxSe74vgjeGjT0NjBNLlvfCOsZ-n_BUiGiqvymjXcWhpwsegY9-y4HUWGdjTv2EhQyU9nSxyERZXwr1KyEBMohiKpPnQ_jBMQC8G9f3iGz9KxPhFQNTds>)

Figure 11. Final iMethod embedding into an online research article

![](<https://lh5.googleusercontent.com/awA7AfrE2nzotpW7E53NBg9ptBdNSFdygpFHHYn2v8X8fhSfipeRPtACer3cDpb5Bvd2zzOkRAdOEPuW7LtAkLQ0TRSp0rI0myjhGW-yRxXzjMkNxg3dqFNjPFxkwndcEC2cUn4B>)

Figure 12. Clicking on the url in research article leads to exactly same page
with loaded data

![](<https://lh6.googleusercontent.com/RGwnEKicm1tOIB3vpcfzek7W8ohjt_4NX8_qWGMkKRvbzWq-dU1L5UVIOFHCQhxtzL43fTH4czyQiDYNWMFeUmcJKN5YK0i4dNo1_P_E-4AJybyXU9Y_zKxEkBHRb7Pp5TLhbPkV>)

### ScienceOpen - USA collaborator

ScienceOpen is a freely accessible research network to share and evaluate
scientific information. It aggregates Open Access and article metadata articles
from a variety of sources, opening them up to public and professional commenting
and discussion. Because ScienceOpen sets a high value on reproducibility but
also believes that problems with research results are often only discovered
after publication we have created a publishing platform to respond flexibly to
the needs of the scientific community. It offers rapid publication with
post-publication peer review and article versioning to respond to critique.

ScienceOpen combines the advantages of a publishing platform, research network,
and content archive in one place and serves as a “Research and Publishing
Network”. It facilitates communication and collaboration among scientists;
manages peer review and manuscript editing, and satisfies the increasing demands
of authors to shorten publication times, to reach a broader audience and to
consult peers for additional input.

The ScienceOpen database currently consists of over 11 million article records.
The core of the database is drawn from the PubMed Central Open Access Data
Subset and arXiv records. Through analysis of the reference structure of this
Open Access core, the ScienceOpen ciation engine adds bibliographic records for
cited papers to the database.  Refined search and filtering tools help
researchers find the information sources that they need and a social network
structure overlayed over the database allows users to interact with the content
via post-publication peer review and curation in collections.

Figure 13 Post-publication peer review: Open reports

![](<https://lh6.googleusercontent.com/aS9vApvP681K8derm9qQPfFQMjiMoWrt7TRk0zvPjNQm0BhkWd-Og6D8hY8pnvai5DYOb7L4mItCOPoxQLrQvkxD6DLev3-gfFyrrzZM3DolJvTinyhE8nU74Svvq3pMkm8Myvu5>)

ScienceOpen further offers Collections curated by editors from the total
articles on the platforms to further serve the research community in assessing
the scientific literature. ScienceOpen Collections provide topic-specific
bundling, editorial management and quality assurance for articles, designed for
post-publication and drawn from a variety of topics, publishers or journals. It
creates a space for researchers to continue to share, discuss and curate
published content.

Figure 14 ScienceOpen Collections

![](<https://lh4.googleusercontent.com/W2fD5M2SjVDPVATZubH3nEf6RVZREHqAeCIYPzjpDSw-sFqKmS6auXObhNClzKt8Ih5aLZ5i8Ihpb7D-0XGmvzpg3M7dpg7WIBPKxp4ZZbFBFRKIl7B1DRnUeltXhxm7BeE0seh9>)

  
In combination with the InsideDNA platform, ScienceOpen can publish articles
vetted by InsideDNA iMethods embedded into the articles and shared during an
article publication process. These articles can be assembled in a Collection and
openly discussed using the ScienceOpen post-publication peer review tools and
versioning to ensure that reproducibility can be easily verified and/or
rectified.

 

Technical aims under OpenSciencePrize initiative
------------------------------------------------

We envision realisation of the following technical aims under OSP initiative:

### Integration of ScienceOpen and InsideDNA

To evaluate the utility of iMethods for researchers, we will run a pilot
integration project between ScienceOpen as an article publishing platform and
InsideDNA Sharing service. We will work closely with researchers and evaluate
whether iMethod publishing is technically convenient and helps peer-review and
re-use of the published content. Based on the feedback, we will iteratively
improve steps involved into the processes of publishing and ensure that iMethod
is viable in a long run.

### Curation at ScienceOpen

ScienceOpen will create a specific InsideDNA Collection where articles published
meeting the requirements may be automatically added and managed by editors
assigned by InsideDNA. A community of interested researchers using methods, data
or code can provide feedback on their experience in reproducing results and
authors can both respond and improve.

### Development of InsideDNA tool publishing and sharing services

Currently, InsideDNA developed an early alpha version of the publishing and
sharing service which is now in internal use only. Under OpenSciencePrize
initiative we plan to finalize publishing service and release beta version for
general public (Appendix 1).

### Development of InsideDNA interoperability connector and database integration

During OpenSciencePrize phase one, we plan to prototype the first version of the
interoperability connector and test it on three public databases:  [Autism
Speaks](<http://research.mss.ng>), [TCGA](<https://tcga-data.nci.nih.gov/tcga>)
and [dbGaP](<http://www.ncbi.nlm.nih.gov/gap>). Interoperability connector will
help to re-use medical and health related genomic data to an unprecedented
extent and provide access for many researchers who previously did not have a
chance to work on such data.

 

Addressing goals of OpenSciencePrize
------------------------------------

### Openness.

Our project will:

-   make systematic re-use of published software, data and settings;

-   make possible settings sharing and method re-use;

-   foster international collaboration between groups via shared projects;

-   provide smaller universities (without cluster) and research groups (without
    server) with a way to do massive genomic analysis;

-   bring equal opportunities for complex research to universities without a
    budget for cluster facilities;

-   integrate existing biological and medical database making it easy to re-use
    open data;

 

### Impact 

Our project will bring numerous benefits to health/healthcare research by:

-   introducing a new way of sharing research methods;

-   making massive re-use of published code, methods and datasets;

-   fostering collaboration between groups;

-   making knowledge and method transfer from research to industrial application
    easier;

-   reducing time for scientists to learn bioinformatics;

-   breaking “IT facility” barriers for starting health
    care/medical/bioinformatic research

-   exposing public health data together with computational power to all
    researchers;

-   making access to research know-how more transparent.

 

### Innovation 

Our main innovations are:

1.  iMethod - an executable and reusable bundle comprising data, code, and
    methods;

2.  iMethod integration into the publication process of a research article and

3.  Automated tool publishing

4.  Open data interoperability connector

 

### Originality

See Appendix 2 for InsideDNA/ScienceOpen features in comparison to existing open
source, free and proprietary solutions.

 

### Technological viability

Three main aspects ensure platform viability:

1.  Google Cloud Engine as the base. Cloud storage containers are very
    persistent storage types accessible irrespective of whether InsideDNA or
    SceinceOpen continue operating

2.  Integration of ScienceOpen and InsideDNA is a first example of how full
    cycle of research publication can become reproducible, open and re-usable.
    By working in close cooperation with researchers we will ensure that
    developed processes are convenient and can be adopted on a regular basis.

3.  User involvement. We will involve tools authors and researchers by providing
    compute credits pool for those who actively maintain their code and share
    research via iMethods.

 

### Resource feasibility

InsideDNA team is working on the platform development since 2014. InsideDNA team
developed a stable beta-release for the [research
platform](<http://www.insidedna.me>) and an early stage prototype for tool
publishing service and sharing service (Appendix 2). Last 6 months, the platform
was publically accessible and we obtained very positive user feedback.
Currently, we work on 3 collaborative research papers that use InsideDNA and
will be published with embedded iMethods [9].

InsideDNA team is supported by Google Inc. with cloud compute credits (see their
letter of recommendation and recommendation from the Infinity team). We will
collaborate with Google Genomics on integration of Autism Speaks, TCGA, dbGaP
databases. The development of the platform during last 2 years confirms our
competence and self-motivation to realise the entire project.

The ScienceOpen publishing network launched in 2014 and has been growing
steadily. It is supported by a strong development team located in Boston. It has
published over 270 items ranging from research articles to posters and peer
review reports.

 

Conclusion and disclaimer 
--------------------------

We believe that current technological barriers to efficient and widespread data
re-use can be overcome. We have the passion, the skills and the team to
eradicate these barriers and move research in life science and biomedical
research forward.

 

References:
-----------

1.  Begley, C. Glenn, Alastair M. Buchan, and Ulrich Dirnagl. "Robust research:
    Institutions must do their part for reproducibility." Nature 525.7567
    (2015): 25.

2.  The Reproducibility and reliability of biomedical research: Improving
    research practice Symposium report, October 2015

3.  Number of clusters counted as number of bioinformatics core facilities from
    omicsmaps.com divided by total number of universities in the world

4.  <https://github.com/InsideDNA/bio_tools>

5.  BIoinformatics infrastructure survey
    <https://docs.google.com/forms/d/10P299OB_cfwC7zyTBAdddo1Wh9py_vUGcTy-yczQoTU/viewanalytics>

6.  ENCODE ftp <https://genome.ucsc.edu/ENCODE/downloads.html>

7.  Stein, Lincoln D., et al. "Data analysis: Create a cloud commons." Nature
    523 (2015): 149-151.

8.  https://github.com/codemeta/codemeta

9.  Hybridization capture using RAD probes (hyRAD), a new tool for performing
    genomic analyses on museum collection specimens. Accepted with minor
    revision to PLOS One and available doi: http://dx.doi.org/10.1101/025551



Appendices. 
------------

Appendix 1. Developmental stage of InsideDNA features

![](<https://lh5.googleusercontent.com/8liGtaSh5PRviEdlKq98DJTALTOH7cfvUnEDVOLPbALraIHuERriV079T6rEo7UW9hzIMGrKEyzpRBjMfCFODrFD4khmRHtnDChcz13YUXqDSe62sUOE5PTmBj8badSwHkItPgrs>)

Appendix 2. Comparison of InsideDNA functionality to existing FOSS and
proprietary solutions

![](<https://lh6.googleusercontent.com/swgoWjjdnHo8gE266BvjQSjtlK64yQXJmPTCKdWQMeOdUAKkQZ1wh1aOkEpZcsieP0OhiJwAlwKt0GRxCZRmemlo1e7TCVcLWVKHRWwWfERZE7njHXh6gR632wdOqLaSeMvvdqVn>)
