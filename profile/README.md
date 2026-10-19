<p align="center">
  <img src="https://raw.githubusercontent.com/algeon-dev/.github/main/profile/algeon-logo.png" alt="Algeon" width="420">
  <br>
  <em>Compose algorithms with SQL.</em><br><br>
  <a href="https://algeon.dev">Website</a> |
  <a href="https://github.com/algeon-dev/algeon">Source</a> |
  <a href="https://docs.rs/algeon-datafusion">API Docs</a>
</p>

Algeon (`/ˈæl.dʒi.ən/`, "AL-jee-on") is a GPU-accelerated query engine built
on [Apache DataFusion](https://datafusion.apache.org/). It runs NVIDIA's
[cuGraph](https://docs.rapids.ai/api/cugraph/stable/),
[cuVS](https://docs.rapids.ai/api/cuvs/stable/) and
[cuML](https://docs.rapids.ai/api/cuml/stable/) algorithms as SQL table
functions next to [cuDF](https://docs.rapids.ai/api/cudf/stable/) relational
execution. One query selects the input, runs the algorithm and joins the
result back. [Introducing Algeon](https://algeon.dev/blog/introducing-algeon)
shows this on public datasets.

## Repositories

| Repository | Contents |
| --- | --- |
| [algeon](https://github.com/algeon-dev/algeon) | The Rust workspace: the DataFusion extension, the `algeon_server` Flight SQL binary, the `algeon-*` crates published on crates.io, and the website. Issues and pull requests go here. |
| [cudf](https://github.com/algeon-dev/cudf), [cugraph](https://github.com/algeon-dev/cugraph), [cuvs](https://github.com/algeon-dev/cuvs) | Forks of the RAPIDS libraries, pinned as submodules of `algeon`. Each `algeon-*` branch carries the changes Algeon's native build needs on top of the upstream release; [Fork changes](https://algeon.dev/reference/forks) lists them. Generic fixes are proposed upstream. |

## Getting started

Algeon requires Linux and a supported NVIDIA GPU.

- **Run the server image** over the Parquet files in the current directory:

  ```bash
  docker run --rm --gpus all -p 127.0.0.1:50051:50051 \
    -v "$PWD:/data:ro" ghcr.io/algeon-dev/algeon-server
  ```

  Check the [host requirements](https://algeon.dev/build/docker#run-the-published-image),
  then submit a query with the
  [client quickstart](https://algeon.dev/integration/flight-sql-server#quickstart).
- **Build from source:** [prerequisites](https://algeon.dev/build/prerequisites)
  and the [build guide](https://algeon.dev/build).
- **Embed in Rust:** the
  [DataFusion session guide](https://algeon.dev/integration/datafusion-session).

## Status

> [!WARNING]
> Algeon is experimental. APIs and query behavior may change incompatibly.
> Compare outputs against trusted reference results. The
> [roadmap](https://algeon.dev/reference/roadmap) lists what changes next.

## Contributing

[CONTRIBUTING.md](https://github.com/algeon-dev/algeon/blob/main/CONTRIBUTING.md)
covers the checkout, conventions and validation, and
[SECURITY.md](https://github.com/algeon-dev/algeon/blob/main/SECURITY.md)
explains how to report a vulnerability privately. Algeon is licensed under
the [Apache License 2.0](https://github.com/algeon-dev/algeon/blob/main/LICENSE).
