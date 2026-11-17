# system_monitor

A simple Bash script that launches a tmux session (or window) with `btop` on top and a GPU monitoring tool below.

It automatically selects the best available GPU monitor (`nvtop`, `amdgpu_top`, `nvidia-smi`, or `intel_gpu_top`) and falls back gracefully if none are present.

## Requirements

- `tmux`
- `btop` (or another full-screen system monitor of your choice — edit the script if you prefer something else)
- Optional GPU tools (the script will use the first one it finds):
  - `nvtop`
  - `amdgpu_top`
  - `nvidia-smi`
  - `intel_gpu_top`

Install them with your package manager. Examples:

```bash
# Debian/Ubuntu
sudo apt install tmux btop nvtop

# Fedora
sudo dnf install tmux btop nvtop

# Arch
sudo pacman -S tmux btop nvtop
```

## Usage

Make the script executable and run it:

```bash
chmod +x system_monitor
./system_monitor
```

- If you are **not** already inside tmux, it creates a new session named `monitor`.
- If you **are** already inside tmux, it creates a new window named `monitor` instead of nesting sessions.

You can also place the script somewhere on your `PATH` (for example `~/bin` or `~/.local/bin`) and invoke it as `system_monitor` from anywhere.

## Customization

- The bottom pane height is controlled by `split_opts`. The current setting uses a percentage (`-p 15`) with a minimum line count (`-l 5`). Change these values to suit your screen.
- To use a different system monitor instead of `btop`, replace the `"btop"` argument in the `tmux` commands.

## License

MIT
