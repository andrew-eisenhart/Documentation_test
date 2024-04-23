---
variables:
  app_name: "APP_1"
  folder_name: "app-1"
  conf_file: "app1_next_runtime.conf"
  execution_time: "1"
  projection_time: "1"
  repetitions: 1
  nextrunner: 
    executable: "app1"
    cmd_args: ["-n 100"]
  exporters:
    OMP_NUM_THREADS: 8
  handoff:
    cmd_args: ["-n 1"]
  exporters:
    OMP_DYNAMIC: 1
---

{{page.variables.app_name}}

## Overview

{{snippet.environment_setup}}

{{snippet.cloning_ns-examples}}

## Building

{{ build_commands() }} - needs folder_name:

### Build options

- `BLOCK_SIZE` (default = `1024`): Lookahead amount for streaming tests

## Running

{{ executable_location() }} - needs executable and folder location

Example run:

{{run_cpu ()}} - needs executable and folder

## Generating mills

{{ merge_conf(".") }} - needs folder name

{{ launch_daemon() }} - needs conf file name

{{ run_optimize(".") }} - needs command line options

{{ status_and_mill_summary_output() }} - needs to reference a file's contents and other variables

{{snippet.Open the profiler markdown}}
