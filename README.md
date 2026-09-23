# Intelligent Memory Management System Using Predictive Page Replacement

A page replacement system that predicts which memory pages will be reused soon and evicts the ones least likely to be needed, instead of relying only on fixed rules like FIFO or LRU.

## Problem

Classic policies (FIFO, LRU, Clock) decide only from past access order. They can evict a page that is about to be used again, causing extra page faults and slowing the system. This project adds a prediction step so eviction is based on expected future reuse.

## How it works

1. **Reference stream:** the simulator reads a sequence of page accesses.
2. **Feature extraction:** for each page it tracks recency, access frequency, and access stride.
3. **Reuse predictor:** a model estimates how soon each page will be used again.
4. **Replacement policy:** on a page fault with full frames, evict the page with the farthest predicted reuse.
5. **Update:** the actual outcome is fed back to improve later predictions.

![Architecture](docs/architecture.png)

## Features

- Predictive replacement policy
- Baseline policies for comparison: FIFO, LRU, (add: Optimal, Clock)
- Configurable number of frames and workload traces
- Page-fault rate and hit-ratio reporting

## Tech stack

- Language: `<add: Python / C++ / Java>`
- Libraries: `<add: NumPy, scikit-learn, matplotlib, etc.>`

## Getting started

```bash
git clone https://github.com/Yatharths07/predictive-page-replacement.git
cd predictive-page-replacement
pip install -r requirements.txt   # adjust to your stack
python main.py --frames 4 --trace traces/sample.txt   # adjust to your CLI
```

## Results

Fill this in with your own measured numbers.

| Policy | Frames | Page faults | Hit ratio |
|--------|--------|-------------|-----------|
| FIFO   | `<n>`  | `<x>`       | `<x>`     |
| LRU    | `<n>`  | `<x>`       | `<x>`     |
| Predictive (ours) | `<n>` | `<x>` | `<x>` |

## Project structure

```
.
├── src/            # simulator, predictor, policies
├── traces/         # sample page-reference traces
├── docs/           # architecture diagram, screenshots
├── requirements.txt
└── README.md
```

## Future work

- Test on real application traces
- Lightweight models suitable for kernel-level use
- Adaptive switching to LRU when prediction confidence is low

## Author

Yatharth
