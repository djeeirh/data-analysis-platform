

# Data Analysis Platform

Welcome to the Data Analysis Platform repository!

The Data Analysis Platform is a powerful and versatile infrastructure framework designed to help data analysts of every kind achieve reproducibility and streamline their workflows. Statistical evaluations, Business Intelligence (BI), Machine Learning (ML), and  Deep Learning (DL): everything is possible. With this platform, you can easily manage and track experiments, collaborate with team members, and build flexible and powerful pipelines based on GitLab.

This platform is entirely **technology agnostic**, making it suitable for use with any tool or language (BYOS - Bring Your Own Software principle). It is also designed with enterprise use in mind and offers easy deployment and built-in security features.

## Goal

The goal of this project is not to create the next "everything you will ever need" tool or something like this. It is more to **start a conversation** about the infrastructure for data analysis projects of all kinds and in all environments. 

Data analysis projects certainly can be done without fancy IDEs, data management through manual file juggling, experiment tracking in excel, script execution via SSH directly on target machines, and collaboration through long email threads. Is this approach efficient? Certainly not. 

Maybe specialized AI plattforms such as [ClearML](https://clear.ml/), [MLRun](https://www.mlrun.org/), [Amazon SageMaker](https://aws.amazon.com/sagemaker/), [Azure ML](https://azure.microsoft.com/en-us/products/machine-learning/) and many others are the solution? Maybe. Some of them are really good and absolutely could cover all your needs. But are they really flexible? Can you manage your data however you want and ensure it belongs only to you? Can you integrate them with the plethora of strange enterprise tools running in your organization? Is it possible to scale and modify them extensively to adapt to your needs and amount of data? Usually, not really.

Then, what is the best data analysis tool out there? I certainly do not know this. This question has no one-size-fits-all answer. Let us start a discussion in this repository. I created this framework to address issues my colleagues and I encountered during our data analysis adventures. However, the main idea was always to make something extensible and adaptable since everyone has other requirements and operational conditions. And you even don not have to use it at all. So just get some inspiration for your endeavor and share some thoughts in the discussions or issues sections.

Let us think together about how to improve data analysis projects. Increase reproducibility, decrease pain, and have more fun. Join me on this journey, and I am sure we will arrive at many interesting solutions and have many exciting conversations.

## Usage

For installation and usage instructions consult the documentation in the `doc/` directory.

Start here:

- [Initial installation and provisioning](doc/provision.md)

## Questions?

If you have any questions or need help, please do not hesitate to ask them in the `Discussions` section.

## Improvements and Suggestions

Please suggest any improvements or express wishes in the Issues section. A pull request with a corresponding implementation or fix is not required but would be appreciated.

## Roadmap

### Important

- [ ] Remove the requirement of public TLS certificates either by integrating self-signed certificates or implementing a no-tls option.
- [ ] Write thorough documentation and some HowTos.
- [ ] Add monitoring of all services.
    - Some users might want to use their existing monitoring infrastructure.
    - Suggestion: Grafana, Prometheus and AlertManager
    - A ready Grafana dashboard for Prometheus metrics ([click](https://grafana.com/grafana/dashboards/1860-node-exporter-full/))

### Security

- [ ] Add access control to the MLflow service (currently, no authentication is available)
    - Idea: use nginx HTTP authentication.
- [ ] Secure the ssh config of the dev-base environment container.
- [ ] Hide the GitLab container registry behind the reverse proxy (currently, it is exposed due to compatibility issues).
    - Idea: Set server location in Minio.
- [ ] Consider adding TLS to Jupyter Notebooks in environment containers for remote development access.
- [ ] Consider the transition to a more zero-trust-like architecture:
    - Remove the reverse proxy and docker compose.
    - Configure security for each service separately (certificates, etc.)
    - Pro:
        - Reduces reliance on docker compose.
        - Allows a more flexible deployment (distribution of services across multiple machines).
    - Contra:
        - Increases management overhead and deployment complexity.
        - Removes some security features of the reverse proxy (see nginx config).
        - Name resolution required (custom DNS?). Currently, docker is handling this.

### Less important

- [ ] Configure dependabot version alerts.
- [ ] Add a `CONTRIBUTING.md` file describing how to contribute to the project.
- [ ] Update `SECURITY.md` with concrete contact details.
- [ ] Add automated tests.
- [ ] Develop a painless version upgrade system.
    - Users might change their local installations (configs, scripts, docker compose, etc.). It should be possible to upgrade to a new version of the Data Analysis Platform without losing local changes (an intelligent merge).
    - Consider upgrades of running production deployments.
- [ ] Develop a backup solution to safely backup data from all services. A painless rollback to a previous version should be possible.

### Least important

- [ ] Use multi-stage docker builds for environment containers to reduce image sizes.
- [ ] Render documentation on GitHub Pages or readthedocs.io.
- [ ] Add linting of code (there is little actual code to analyze, hence the low priority).
- [ ] Add static code analysis (there is little actual code to analyze, hence the low priority).
- [ ] Add missing service redirect in nginx config (currently the first configured server (pgadmin) is returned).



