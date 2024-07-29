This minimalist template is meant to loosely follow nf-core guidelines without fully adhering to the open-source policy.
It was created using nf-core create while skipping a maximum of steps, then by removing the modules and as many non-generic options as possible.

Note that nf-core lint requires at least one nf-core module to be installed in order to work. If you would like a version of the template that works with lint, check out the [multiqc branch] (https://github.com/FelixAntoineLeSieur/ferlab-mypipeline/pull/1).

### Once you have cloned the template, you will need to:
- Replace all instances of "mypipeline" with the name of your pipeline, including the filename in the workflow directory. 
- Make sure your input file samplesheet follows the validation described in `assets/schema_input.json`. Right now, it follows the sample sheet requirement from [nf-core/sarek](https://github.com/nf-core/sarek/blob/master/assets/schema_input.json), which accepts many file types.
- Create the input channel from your samplesheet. The validation of your samplesheet and the creation of the input channel occurs in the `PIPELINE_INITIALISATION` process which is defined in `subworkflows/local/utils_nfcore_mypipeline_pipeline/main.nf`
- Install modules with either:
1. `nf-core module install [moduleName]` (see https://nf-co.re/modules/)
2. `nf-core create module` and follow the steps

- Make sure to use `include {[process_name]} from [module_path]` where needed (most likely your main workflow).
- For every parameter used in the module, make sure to include them in nextflow.config.
- Next, use `nf-core schema build` to incorporate every new parameter to the nextflow_schema.json, along with any description, help info and restriction needed.
- You should make sure the pipeline can run with `-profile test`, by providing a small set of data on which the pipeline can run. Nf-core provides sets of [test-data you can link to](https://github.com/nf-core/test-datasets)
- Ideally, use `nf-core lint`. If needed, add the required tests to ignore in .nf-core.yml.
- Create your own repo and push your pipeline. 
- Modify Changelog, readme, and make sure to path to your repo instead of here. 



## Introduction

**ferlab/mypipeline** is a bioinformatics pipeline that ...

<!-- TODO nf-core:
   Complete this sentence with a 2-3 sentence summary of what types of data the pipeline ingests, a brief overview of the
   major pipeline sections and the types of output it produces. You're giving an overview to someone new
   to nf-core here, in 15-20 seconds. For an example, see https://github.com/nf-core/rnaseq/blob/master/README.md#introduction
-->

<!-- TODO nf-core: Include a figure that guides the user through the major workflow steps. Many nf-core
     workflows use the "tube map" design for that. See https://nf-co.re/docs/contributing/design_guidelines#examples for examples.   -->
<!-- TODO nf-core: Fill in short bullet-pointed list of the default steps in the pipeline -->


## Usage

> [!NOTE]
> If you are new to Nextflow and nf-core, please refer to [this page](https://nf-co.re/docs/usage/installation) on how to set-up Nextflow. Make sure to [test your setup](https://nf-co.re/docs/usage/introduction#how-to-run-a-pipeline) with `-profile test` before running the workflow on actual data.

<!-- TODO nf-core: Describe the minimum required steps to execute the pipeline, e.g. how to prepare samplesheets.
     Explain what rows and columns represent. For instance (please edit as appropriate):

First, prepare a samplesheet with your input data that looks as follows:


Now, you can run the pipeline using:

<!-- TODO nf-core: update the following command to include all required parameters for a minimal example -->

```bash
nextflow run ferlab/mypipeline \
   -profile <docker/singularity/.../institute> \
   --input samplesheet.csv \
   --outdir <OUTDIR>
```

> [!WARNING]
> Please provide pipeline parameters via the CLI or Nextflow `-params-file` option. Custom config files including those provided by the `-c` Nextflow option can be used to provide any configuration _**except for parameters**_;
> see [docs](https://nf-co.re/usage/configuration#custom-configuration-files).

## Credits

ferlab/mypipeline was originally written by me.

We thank the following people for their extensive assistance in the development of this pipeline:

<!-- TODO nf-core: If applicable, make list of people who have also contributed -->

## Contributions and Support

If you would like to contribute to this pipeline, please see the [contributing guidelines](.github/CONTRIBUTING.md).

## Citations


<!-- TODO nf-core: Add bibliography of tools and data used in your pipeline -->

> **The nf-core framework for community-curated bioinformatics pipelines.**
>
> Philip Ewels, Alexander Peltzer, Sven Fillinger, Harshil Patel, Johannes Alneberg, Andreas Wilm, Maxime Ulysse Garcia, Paolo Di Tommaso & Sven Nahnsen.
>
> _Nat Biotechnol._ 2020 Feb 13. doi: [10.1038/s41587-020-0439-x](https://dx.doi.org/10.1038/s41587-020-0439-x).
