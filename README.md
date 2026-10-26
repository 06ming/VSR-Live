# VSR-Live

**VSR-Live** is an aligned multi-resolution frame dataset for live video super-resolution research.

## Dataset

The dataset contains 10,813 temporally aligned frame triplets:

| Directory | Resolution | Frames | Description |
|---|---:|---:|---|
| `HR_1080p/` | 1920 × 1080 | 10,813 | High-resolution reference frames |
| `LR_720p/` | 1280 × 720 | 10,813 | 720p live-stream frames |
| `LR_360p/` | 640 × 360 | 10,813 | 360p live-stream frames |

Frames are losslessly stored as PNG images decoded from the corresponding video streams. The three streams have matching frame counts, timestamps, and frame-number-based filenames. The data payload is approximately 45.4 GB (42.3 GiB), plus the frame index.

`index.csv` maps each `frame_id` to its HR, LR720, and LR360 image paths.

## Download

Download all `VSR-Live_frames_*.tar` assets and `VSR-Live_metadata.tar` from the [v1.0.0 release](https://github.com/oYTYo/VSR-Live/releases/tag/v1.0.0). Each frame archive contains a disjoint range of frame IDs and can be extracted into the same output directory:

```bash
mkdir VSR-Live-data
for f in VSR-Live_frames_*.tar; do tar -xf "$f" -C VSR-Live-data; done
tar -xf VSR-Live_metadata.tar -C VSR-Live-data
```

On Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force .\VSR-Live-data | Out-Null
Get-ChildItem .\VSR-Live_frames_*.tar | ForEach-Object { tar -xf $_.FullName -C .\VSR-Live-data }
tar -xf .\VSR-Live_metadata.tar -C .\VSR-Live-data
```

The extracted structure is:

```text
VSR-Live-data/
├── HR_1080p/
├── LR_720p/
├── LR_360p/
└── index.csv
```


The data is publicly hosted for access. No separate open data license is specified in this release; public availability alone does not grant reuse rights. Contact the repository owner to discuss usage terms and attribution.

## Citation

If you use VSR-Live, please cite our work **VSRBuff**
