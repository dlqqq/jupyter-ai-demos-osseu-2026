# Jupyter AI Demos @ OSS-EU 2026

Demos of [Jupyter AI](https://github.com/jupyterlab/jupyter-ai) and AI agents driving JupyterLab, shown at OSS-EU 2026.

## Setup

Requires [pixi](https://pixi.sh).

```bash
git clone https://github.com/dlqqq/jupyter-ai-demos-osseu-2026
cd jupyter-ai-demos-osseu-2026
pixi install
pixi run lab
```

`pixi run lab` starts JupyterLab with Jupyter AI. Dependencies come from conda-forge wherever possible.

## Connect Claude Code / Codex to JupyterLab

Jupyter AI ships [`jupyter-server-mcp`](https://github.com/jupyter-ai-contrib/jupyter-server-mcp), which starts an MCP server on `localhost:3001` alongside JupyterLab. It gives agents tools to create, edit and run notebooks and to execute JupyterLab commands.

Start JupyterLab first (`pixi run lab`), then start your agent from this directory.

**Claude Code:** this repo includes a [`.mcp.json`](.mcp.json), so just run `claude` here and approve the `jupyter-mcp` server. To add it manually:

```bash
claude mcp add jupyter-mcp -- pixi run python -m jupyter_server_mcp.proxy
```

**Codex:**

```bash
codex mcp add jupyter-mcp -- pixi run python -m jupyter_server_mcp.proxy
```

The proxy finds the running Jupyter server automatically. To connect directly over HTTP instead, use `http://localhost:3001/mcp`.

## Demo 1: Finding gravitational waves with notebooks

[`gravitational_waves.ipynb`](gravitational_waves.ipynb) reproduces the first detection of gravitational waves (GW150914, 2017 Nobel Prize in Physics) from LIGO's open data. It combines narrative, LaTeX, images, plots, audio of the "chirp" and an interactive widget for weighing the black holes.

Data is stored in [`data/`](data/), so the notebook runs offline. The last section suggests follow-up analyses to drive with Claude or Codex through the MCP server.

## Demo 2: Quantitative finance via Jupyter AI

We also showed a Jupyter AI persona for quantitative finance, which prices securities and optimizes portfolios from plain-English requests in the chat. Its source code is still in development and isn't available yet.

## Credits

Gravitational-wave data from the [Gravitational Wave Open Science Center](https://gwosc.org). Image credits are in the notebook.
