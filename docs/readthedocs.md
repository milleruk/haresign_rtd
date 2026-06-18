# Read the Docs Setup

This documentation set is ready to publish on Read the Docs using MkDocs.

If the main application repository is private, the simplest public setup is to
copy the documentation files into a separate public repository and connect that
repository to Read the Docs.

## Files

| File | Purpose |
|---|---|
| `.readthedocs.yaml` | Read the Docs build configuration. |
| `mkdocs.yml` | MkDocs site configuration and navigation. |
| `docs/requirements.txt` | Python packages installed by Read the Docs for the docs build. |
| `docs/index.md` | Documentation homepage. |
| `docs/api.md` | Developer API guide. |

## Import the Project

### Option A: Separate Public Docs Repository

Use this option when the application repo should remain private but the docs
should be public.

Copy these files and folders into the public documentation repository:

```text
.readthedocs.yaml
mkdocs.yml
docs/
```

The public docs repo does not need the Django project code. The API pages link
to the live OpenAPI schema on `https://haresign.net/`, so the generated docs
remain useful without importing private source files.

After copying, update these values in `mkdocs.yml` if needed:

| Setting | Notes |
|---|---|
| `site_url` | The final Read the Docs URL for the public docs project. |
| `repo_url` | The public docs repository URL. |
| `repo_name` | The public docs repository name shown in the docs UI. |

### Option B: Main Repository

Use this option only if Read the Docs has access to the private app repository
and the intended documentation visibility is acceptable.

1. Open `https://app.readthedocs.org/dashboard/`.
2. Choose **Import a Project**.
3. Select the Git repository for this project.
4. Keep the default branch selected.
5. Build the project.

Read the Docs will detect `.readthedocs.yaml`, install `docs/requirements.txt`,
and build the MkDocs site from `mkdocs.yml`.

## Expected Public URL

The `mkdocs.yml` file currently assumes this canonical docs URL:

```text
https://haresign-rtd.readthedocs.io/
```

If the Read the Docs project slug is different, update `site_url` in
`mkdocs.yml` after importing the project.

## Local Preview

Install the docs dependencies:

```bash
python -m pip install -r docs/requirements.txt
```

Serve locally:

```bash
mkdocs serve
```

Build strictly:

```bash
mkdocs build --strict
```

## Live API Schema

The Read the Docs site is the narrative developer guide. The live API schema is
served by Django:

- `https://haresign.net/api/docs/`
- `https://haresign.net/api/redoc/`
- `https://haresign.net/api/schema/`
