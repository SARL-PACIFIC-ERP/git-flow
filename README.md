# Git workflows for Pacific ERP

This repository contains reusable workflows to be used in our other repositories in order to comply with our git flow policy. 

## Pacific ERP git flow

Keep in mind that in odoo.sh, branches are environments. 

### Branches

- A `production` branch, for the production environement
- A `staging` branch for the staging environment
- Several `feat/my-feature`, `fix/my-fix` as development environments

### Usage

- All developments starts on a dedicated branch
- Development branches are merged in staging with a merge commit
- `staging` is rebased onto development branches before merging
- Publish a version tag (ex: `v18.0.1.0.0`) on `staging` head to automatically deploy `staging` into `production`  
  - Any tag not complying to the pattern above will be ignored
  - If tag does not match `staging` head, deployment will fail and throw an error

### Constrains

- **Never work on `production`**. No clone, no push, not even a tiny little fetch. Use tags for workflow automation.
- `production` and `staging` should always be identical after a deployment.
- **Do not edit code through GitHub web UI**, no matter how much it asks you to do it.
