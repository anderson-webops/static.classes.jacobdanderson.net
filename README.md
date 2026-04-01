# static.classes.jacobdanderson.net

Static asset repository for `static.classes.jacobdanderson.net`.

## What Lives Here

- downloadable project media such as GIFs and MP4s
- CSV and dataset files served directly from the static host
- archive files such as `assets.zip`

## Git and Storage Notes

- Large binary assets in this repo are tracked with Git LFS. Do not remove or bypass the rules in [`.gitattributes`](./.gitattributes).
- After cloning, run `git lfs pull` before assuming the working tree is complete.
- Use `git lfs ls-files` when verifying that newly added large media is being tracked correctly.

## Common Workflow

```bash
git lfs pull
git status
git add <files>
git commit -m "..."
git push origin main
```

## Operational Notes

- There is no build step or package manager in this repo.
- Keep public filenames stable when URLs are already referenced from the main classes site.
- Avoid committing editor metadata or other local-only files.
