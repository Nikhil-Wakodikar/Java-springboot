# CI/CD

## What is CI/CD?

CI/CD stands for **Continuous Integration** and **Continuous Delivery/Deployment**.

It is a software development practice that automates the process of:

- Building code
- Testing code
- Preparing releases
- Deploying applications

Instead of manually building, testing, and deploying an application whenever code changes, CI/CD performs these tasks automatically through a pipeline.

## CI/CD Workflow

1. **Developer writes code**
   - Angular
   - React
   - .NET
   - Other technologies

2. **Developer pushes code to Git**
   - GitHub
   - Azure DevOps
   - GitLab
   - Other Git providers

3. **Continuous Integration**
   - Install dependencies
   - Build the application
   - Run automated tests
   - Report any failures

4. **Continuous Delivery or Deployment**
   - Prepare a release
   - Deploy to a testing or staging environment
   - Deploy to production when appropriate

5. **Application is ready or live**
   - Testing environment
   - Staging environment
   - Production environment

---

## What is Continuous Integration (CI)?

Continuous Integration means that developers frequently merge their code changes into a shared repository, where automated checks validate the changes.

### Example: Angular CI Pipeline

1. A developer modifies an Angular component.
2. The developer pushes the changes to GitHub.
3. The CI pipeline automatically installs dependencies.
4. The pipeline runs the build and automated tests.
5. If something fails, the pipeline reports the failure.

Example commands:

```bash
npm ci
npm run build
npm test
```

The exact commands depend on the project configuration.

### Why CI Matters

CI helps catch:

- Integration problems
- Build failures
- Failing automated tests
- Dependency issues
- Configuration problems

It identifies problems early, before the code reaches production.

---

## What is Continuous Delivery (CD)?

The term **CD** has two commonly used meanings:

### Continuous Delivery

The application is automatically:

- Built
- Tested
- Prepared for release

Production deployment usually requires:

- Manual approval
- A deliberate release action
- A deployment button or process

### Continuous Deployment

Every change that passes the required automated checks is deployed to production automatically.

It does not usually require manual release approval.

| Feature | Continuous Delivery | Continuous Deployment |
|---|---|---|
| Build and testing | Automated | Automated |
| Release preparation | Automated | Automated |
| Production deployment | Requires manual approval or action | Fully automated |
| Human involvement | Required before production deployment | Minimal or none |
| Release risk | Lower due to controlled deployment | Lower if automated testing is comprehensive |

---

## What is `npm ci`?

`npm ci` means **Clean Install**.

It installs project dependencies using the exact dependency versions recorded in `package-lock.json`.

```bash
npm ci
```

### What `npm ci` Does

1. Removes the existing `node_modules` folder.
2. Reads `package-lock.json`.
3. Installs the locked dependency versions.
4. Fails if the lockfile is inconsistent with `package.json`.

### Why It Is Used in CI/CD

`npm ci` provides:

- A clean dependency installation
- Reproducible builds
- Consistent dependency versions
- Faster and more predictable CI setup
- Better protection against lockfile inconsistency

### Interview Answer

> `npm ci` performs a clean, reproducible dependency installation and is ideal for CI/CD pipelines because it uses the exact versions recorded in `package-lock.json`.
