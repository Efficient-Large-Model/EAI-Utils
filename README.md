# EAI-Tools

A toolkit to boost the development of Efficient AI Group.

## Installation

```bash
pip install eai-tools
```

## Features

### Command Line Tools

#### `eai.run` - Run Commands with SLURM Support

A utility for running commands with SLURM support and job management.

```bash
eai.run [options] <command>

Options:
  --job-name, -J       Name of the job (default: eai-test)
  --nodes, -N          Number of nodes to request (default: 1)
  --gpus-per-node     GPUs per node (default: 8)
  --mode, -m          Mode of operation (default: train)
  --time, -t          Time limit for the job (format: HH:MM:SS, default: 4:00:00)
  --timedelta         Time buffer in minutes (default: 10)
  --output-dir        Directory for output files
  --max-retry         Maximum number of retries (-1: auto-select based on mode)
  --pty              Run in interactive mode
  --uuid             Use singleton dependency
  --email            Email address for job notifications
```

Example:
```bash
# Run a training command with SLURM
eai.run -J my_training -N 1 --gpus-per-node 4 -t 12:00:00 python train.py

# Run an interactive session
eai.run --pty bash
```

#### `eai.upload` - Upload Files to Hugging Face

A tool for uploading files and models to Hugging Face repositories.

```bash
eai.upload [options] <local_folder>

Options:
  --model-name        Custom name for the model (default: folder name)
  --repo-type        Type of repository [model|dataset]
  --repo-org         Organization name (default: Efficient-Large-Model)
  --repo-id          Full repository ID (overrides org/model-name)
  --root-dir         Root directory for relative paths
  --token            Hugging Face API token
  -e, --exclude      Patterns to exclude (can be specified multiple times)
  --fast-check       Skip hash verification for existing files
  --sleep-on-error   Sleep and retry on upload errors
```

Example:
```bash
# Upload a model
eai.upload ./my_model --model-name "my-awesome-model" --repo-type model

# Upload a dataset with custom exclusions
eai.upload ./dataset --repo-type dataset -e "*.tmp" -e "cache/*"
```

## Environment Variables

- `VILA_SLURM_ACCOUNT`: Required for SLURM jobs - specifies the account to use
- `VILA_SLURM_PARTITION`: Required for SLURM jobs - specifies the partition to use
- `NO_SLURM`: Set to any value to disable SLURM integration
- `WANDB_PROJECT`: Project name for Weights & Biases logging
- `WANDB_ENTITY`: Entity name for Weights & Biases logging
- `WANDB_NAME`: Run name for Weights & Biases logging

## Contributing

Please visit our [GitHub repository](https://github.com/Efficient-Large-Model/EAI-Utils) for contribution guidelines and to report issues.

## License

This project is licensed under the Apache License 2.0 - see the LICENSE file for details.