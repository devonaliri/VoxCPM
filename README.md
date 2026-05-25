<h2 align="center">VoxCPM2: Tokenizer-Free TTS for Multilingual Speech Generation, Creative Voice Design, and True-to-Life Cloning</h2>

<p align="center">
  <b>English</b> | <a href="./README_zh.md">中文</a>
</p>

<p align="center">
  <a href="https://github.com/OpenBMB/VoxCPM/"><img src="https://img.shields.io/badge/Project%20Page-GitHub-blue" alt="Project Page"></a>
  <a href="https://huggingface.co/spaces/OpenBMB/VoxCPM-Demo"><img src="https://img.shields.io/badge/Live%20Playground-Demo-orange" alt="Live Playground"></a>
  <a href="https://voxcpm.readthedocs.io/en/latest/"><img src="https://img.shields.io/badge/Docs-ReadTheDocs-8CA1AF" alt="Documentation"></a>
  <a href="https://huggingface.co/openbmb/VoxCPM2"><img src="https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-VoxCPM2-yellow" alt="Hugging Face"></a>
  <a href="https://modelscope.cn/models/OpenBMB/VoxCPM2"><img src="https://img.shields.io/badge/ModelScope-VoxCPM2-purple" alt="ModelScope"></a>
  <a href="https://openbmb.github.io/voxcpm2-demopage/"><img src="https://img.shields.io/badge/DemoPage-Audio Samples-red"></a>
  
</p>

<div align="center">
  <img src="assets/voxcpm_logo.png" alt="VoxCPM Logo" width="35%">
  <br><br>
  <a href="https://trendshift.io/repositories/17704" target="_blank"><img src="https://trendshift.io/api/badge/repositories/17704" alt="OpenBMB%2FVoxCPM | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>
</div>

<br>

<p align="center">
  👋 Join our community for discussion and support!
  <br>
  <a href="./assets/feishu-group.png" style="display:inline-block;vertical-align:middle; margin-left: 10px;">
    <img src="./assets/feishu-logo.png" width="16" height="16" style="vertical-align:middle;"> Feishu
  </a>
  &nbsp;|&nbsp;
  <a href="https://discord.gg/KZUx7tVNwz" style="display:inline-block;vertical-align:middle;">
    <img src="./assets/discord-logo.png" width="16" height="16" style="vertical-align:middle;"> Discord
  </a>
</p>

> **Personal fork note:** I'm using this project to experiment with Voice Design and multilingual synthesis for a side project. Main areas of interest: Voice Cloning quality and 48kHz output pipeline.
>
> **My setup:** Running inference on a single RTX 4090 (24GB VRAM). I've found that setting `num_diffusion_steps=10` gives a good speed/quality tradeoff for quick iteration, while `num_diffusion_steps=25` is better for final outputs.
>
> **Tip (personal):** If you're getting OOM errors on 24GB VRAM with long inputs, try chunking the input text at sentence boundaries (~150 chars) and concatenating the output audio. Works well enough for my use case.
>
> **Tip (cloning):** For best voice cloning results, I've had the most success with reference audio that is 8–12 seconds long, recorded in a quiet environment with minimal reverb. Shorter clips (<5s) tend to produce inconsistent timbre across sentences.
>
> **Tip (speed vs. quality):** I also tested `cfg_scale` values — dropping from the default `3.0` to `2.0` noticeably speeds up generation with only a minor quality dip, which is fine for draft/preview runs. Sticking with `3.0` (or even `3.5`) for anything I actually want to keep.

VoxCPM is a **tokenizer-free** Text-to-Speech system that directly generates continuous speech represent