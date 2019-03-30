# Sample CWL Pipelines that work with BLAST.
This directory contains a collection of sample Common Workflow Language (CWL) pipelines that make use of a dockerized version of BLAST.  The samples are also supposed to be simple, so you can easily understand them and start modifying them.

If you are new to CWL, you may want to start by looking at some of the resources listed at the end of this page.

### Why a workflow language?
Many pipeline are written in an ad hoc manner using the scripting language at hand.  In the 90's it was PERL, today it's PYTHON. There's nothing inherently wrong with the scripting languages, but a workflow language (e.g., CWL) provides a framework that is easier for other people to understand and performs more checking on input. Additionally, the CWL framework results in pipeline that are more compliant with [FAIR principles][fair_priniciples]

### What's here for me to look at
Enough talk.  What's in this directory that I should look at?  

First, you should take a quick read through the [CWL User Guide][cwl_man].  Then, you could start by looking at a simple BLASTP search.  Every CWL task requires two files.  The first one specifies the tools and the structure of the work.  The second specifies the arguments to your tools.  For the BLASTP search, you'd execute:

   ```bash
   cwl-runner blastp_docker.cwl blastp_docker_input.yml
   ```

This will just produce normal BLAST output.  That's good, but it would be more exciting to run a BLASTP search, then do something with the results.  The command below runs BLASTP, the parses the tabular output with a python script:

   ```bash
   cwl-runner simple_two_step.cwl simple_two_step_input.yml
   ``` 




Every CWL 


### Resources
* [CWL User Guide][cwl_man] 
* [Video on CWL][cwl_video] 
* [BLAST docker documentation][docker_man]
* [NCBI workbench documentation][workbench_man]

[cwl_man]: https://www.commonwl.org/user_guide/
[cwl_video]: https://www.youtube.com/watch?v=jfQb1HJWRac&feature=youtu.be
[docker_man]: https://github.com/ncbi/docker/blob/master/blast/README.md
[workbench_man]: https://github.com/ncbi/docker/tree/master/ncbi-workbench
[fair_principles]: https://www.force11.org/group/fairgroup/fairprinciples


