# Sample CWL Pipelines that work with BLAST.
This directory contains a collection of sample Common Workflow Language (CWL) pipelines that make use of a dockerized version of BLAST.  The samples are also supposed to be simple, so you can easily understand them and start modifying them.

If you are new to CWL, you may want to start by looking at some of the resources listed at the end of this page.

### Why a workflow language?
Many pipeline are written in an ad hoc manner using the scripting language at hand.  In the 90's it was PERL, today it's PYTHON. There's nothing inherently wrong with the scripting languages, but a workflow language (e.g., CWL) provides a framework that helps you break your task up into distinct steps that are easier to maintain and performs more checking on input. Additionally, the CWL framework results in pipeline that are more compliant with [FAIR principles][fair_principles]

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

You can even modify the python script (it's called parse_blast_report.py) to make it do something else.You can also add steps to this workflow.  

Also, you are not limited to the CWL modules in this directory or the ones you write.  There's a bunch of CWL modules [here][cwl_mods].  One of the workflows in this directory (magicblast2bami.cwl) uses the samtools workflows from that directory to produce a sorted/indexed BAM file from the original SAM file that Magic-BLAST produces.  These modules use a dockerized version of samtools, so you don't even need to compile and install samtools! 



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
[cwl_mods]: https://github.com/common-workflow-language/workflows/tree/master/tools


