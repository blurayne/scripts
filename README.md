# Scripts

## Gitlab Utilities

### `bin/glab-codesearch`

> Gitlab Code Search spiced up for shell with syntax highlighting (using bat) and Regex Search (oniguruma)

What can it do better than web-based Gitlab Codesearch?

- Added Regular expressions
  *(can search in search results or full files)*
- Download full files
  - automatic, never or forced
  - save those files to a local directory (for further processing)
  - or output as tarball 
- Different output formats
  - Just list projects involved
  - Just list all files involved
  - JSON for further processing
  - Filename on STDERR while matched file on STDOUT 
    (which allows for `grep`'ing the STDOUT part while displaying the filename)

### `bin/glab-inspect-ci`

Helper to inspect or help debug failing Gitlab Pipelines/Jobs/Variables to reproduce failing jobs

-  `glab-inspect-ci myorg/mygroup/mysubgroup/myproject` 
  Traverses through parents groups and project and outputs set CI variables

-  `glab-inspect-ci https://gitlab.com/myorg/mygroup/mysubgroup/myproject/-/pipeline/<ID>` 
  Additionally gets merged CICD YAML, Files/Templates involved in pipeline, Pipeline Vars *(respecting protected branch)* 

-  `glab-inspect-ci https://gitlab.com/myorg/mygroup/mysubgroup/myproject/-/job/<ID>` 

  Additionally shows merged job, job vars …

### `bin/gitlab-runner-local-oci-exec`

Execute Gitlab job(s) locally using `fuse-overlayfs` and `podman` (or `docker`).

Note: `gitlab-runner exec` command was [removed in v17.0 #385235](https://gitlab.com/gitlab-org/gitlab/-/issues/385235) 

But they have another epic dealing with [local pipeline execution #2797](https://gitlab.com/gitlab-org/gitlab-runner/-/issues/2797) ([blueprint](https://gitlab.com/gitlab-org/gitlab/-/blob/ci-local-pipeline-exeuction/doc/architecture/blueprints/ci_local_pipeline_execution/ci_local_pipeline_execution.md)) 
*(but I don't agree uploading artifacts won't be possible since `gitlab-runner-local-oci-exec` exactly did that!)*

### `bin/gitlab-pipeline`

Meanwhile superseded by https://gitlab.com/gitlab-org/cli/-/tree/main/docs/source/ci

I wrote this thingy long before.

## FAQ

##### Why not adding this to official [glab CLI](https://gitlab.com/gitlab-org/cli) ([docs](https://docs.gitlab.com/ee/editor_extensions/gitlab_cli/)) ?

BASH is faster to implement for me and allows for quicker adjustments to tweak user-interface (params, formatting)

Also would need to deal with Gitlab Community / Workflow / DIscussions.
