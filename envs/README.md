# envs

Conda environment files for people who do not use Pixi. Generate them from
`pixi.toml` instead of writing them by hand, for example:

    pixi workspace export conda-environment envs/environment.yml

`pixi.toml` and `pixi.lock` stay the source of truth.

## For Conda and Mamba users

`pipeline.yml` is exported from `pixi.toml` (`pixi workspace export conda-environment -e pipeline envs/pipeline.yml`).
It carries version ranges. Build it with
`conda env create -p ./conda-env -f envs/pipeline.yml`.

`explicit/` holds exact package lists, one per platform, exported from `pixi.lock`
(`pixi workspace export conda-explicit-spec -e pipeline envs/explicit`). Build with
`conda create -p ./env --file envs/explicit/pipeline_<platform>_conda_spec.txt`
and use the file for your own platform only.
