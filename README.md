# Algorithm API documentation

This is the base repository for one Mintlify deployment that combines:

- [`DeweyMarco/mintlify-multi-repo-1`](https://github.com/DeweyMarco/mintlify-multi-repo-1) at `/merge-sort`
- [`DeweyMarco/mintlify-multi-repo-2`](https://github.com/DeweyMarco/mintlify-multi-repo-2) at `/shortest-path`

The root [`docs.json`](./docs.json) owns the shared theme and product navigation. Each product uses a `sourceRef` to insert the groups from the corresponding repository's `docs/docs.json`.

## Mintlify setup

Multi-repository deployments require a Mintlify Enterprise plan. In the Mintlify dashboard, open **Settings → Git settings** and configure these three sources:

| Repository | Base source | docs.json directory | URL path |
| --- | --- | --- | --- |
| `DeweyMarco/mintlify-multi-repo-main` | Yes | Repository root | `/` |
| `DeweyMarco/mintlify-multi-repo-1` | No | `docs` | `merge-sort` |
| `DeweyMarco/mintlify-multi-repo-2` | No | `docs` | `shortest-path` |

All three sources must use the `main` branch and the Mintlify GitHub App must have access to each repository. After saving the sources, Mintlify deploys the combined site.

## Local development

Preview the shared shell and landing page from this repository:

```bash
mint dev
```

Run each source site from its own docs directory to preview its full content:

```bash
cd ../mintlify-multi-repo-1/docs
mint dev
```

```bash
cd ../mintlify-multi-repo-2/docs
mint dev
```

The combined `sourceRef` navigation is assembled during a Mintlify multi-repository deployment. A local preview of this base repository shows the shared shell and landing page, but omits the two remote products.
