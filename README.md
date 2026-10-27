<img src="kimun/static/registro/img/logo.svg" alt="Kimün logo" width="90">

# Kimün

**Observation records and learning trajectories for early childhood education.**

Kimün helps educators organize notes about each child's learning. It combines child profiles, classroom summaries, and educator-reviewed observations with AI-assisted transcription and learning-level suggestions.

Built collaboratively during **AWS Breaking Barriers Chile 2026**, for **Fundación Integra's learning trajectories challenge**. The application is in Spanish.

## Demo availability

The hackathon demo ran on AWS resources provided for the event. **There is currently no public hosted demo.** This repository contains the prototype's source code and sample data so it can be explored locally or configured with your own AWS resources.

## Features

- Record notes through text, photos of handwritten records, or audio.
- Review and correct observations organized by AI.
- Follow individual learning progress and compare classroom summaries.
- Review suggested learning levels backed by accepted observations.
- Prepare printable reports for families.

**Educators make the final assessment decisions.** AI suggestions never change validated levels automatically.

## Running the project

| Mode | What is available |
|---|---|
| Local exploration, without AWS | Seeded child profiles, classroom dashboards, existing evidence, manual level decisions, and family reports. |
| AI processing, with your own AWS setup | Transcription, structuring new notes into observations, and generating learning-level suggestions. Requires AWS credentials, service permissions, and background workers. |

For local exploration, install **Python 3.12**, download or clone this repository, and follow the [local setup instructions](docs/guia_tecnica.md#install-and-run-locally). They cover installation, loading fictional sample data, and signing in with the generated demo credentials.

New notes can be saved locally, but **they remain pending until the AI workers run**. There is no offline substitute for the AWS processing pipeline. See [AI setup](docs/guia_tecnica.md#start-the-background-workers) for the configuration required; AWS usage may incur charges.

## Built with

Python · Django · HTMX · SQLite · Amazon Bedrock · Amazon Transcribe · Amazon S3.

## Project status

A **hackathon prototype**, with assessment rules that have not been institutionally validated. Privacy, retention, and infrastructure need further work before using real child data.

Local verification on **October 26, 2026**: **1,230 tests passed** with simulated AWS clients and network access blocked. This does not verify a live AWS deployment. See the [verification record](docs/preparacion_publicacion.md).

## Team and credits

Developed collaboratively by **Camilo-hc, Glo0om, HfRretr0, blu2718, and fpereira3**.

Original code and development history: [blu2718/bbc-aws-2026](https://github.com/blu2718/bbc-aws-2026). This portfolio edition uses an independent Git history and preserves credit to the original team.

Thanks to Fundación Integra for the challenge and materials, and to AWS Breaking Barriers Chile for hosting the hackathon.

## Documentation and license

[Technical guide](docs/guia_tecnica.md) · [AWS infrastructure](infra/README.md) · [Project context](contexto/INDICE.md) · [MIT license](LICENSE) · [Third-party notices](THIRD_PARTY_NOTICES.md)
