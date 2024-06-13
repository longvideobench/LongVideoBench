<div align="center">
  <h1>LongVideoBench: A Benchmark for Long-context Interleaved Video-Language Understanding</h1> 
    
<div style="width: 50%; text-align: center; margin:auto;">
      <img style="width: 50%" src="logo.png">
</div> 
    
<a href="https://huggingface.co/spaces/longvideobench/LongVideoBench">LongVideoBench Interactive Leaderboard.</a>

  <div>
      <a href="https://scholar.google.com.hk/citations?user=wth-VbMAAAAJ" target="_blank">Haoning Wu</a>,
      <a href="https://scholar.google.com/citations?user=h5XtaUUAAAAJ" target="_blank">Dongxu Li</a>,
    <a href="https://scholar.google.com/citations?user=Po65v_MAAAAJ" target="_blank">Bei Chen</a>,
    <a href="https://scholar.google.com/citations?user=MuUhwi0AAAAJ" target="_blank">Junnan Li</a>

  </div>

    
<div>
   <a href="https://HuggingFace.co/datasets/longvideobench/LongVideoBench"><strong>Dataset Release on HuggingFace</strong></a>  | <a href="https://longvideobench.github.io/"><strong>Homepage</strong></a> | <a href="https://huggingface.co/spaces/longvideobench/LongVideoBench"><strong>HuggingFace Leaderboard</strong></a>
   </div>   
    
    
    
<h2>(left) An referring reasoning question. (right) Results with different input frames.</h2> 
<div style="width: 75%; text-align: center; margin:auto;">
      <img style="width: 75%" src="teaser.png">
</div> 

<h2>Initial Leaderboard (view more on <a href="https://huggingface.co/spaces/longvideobench/LongVideoBench"><strong>HuggingFace Leaderboard</strong></a>)</h2> 

<div style="width: 100%; text-align: center; margin:auto;">
      <img style="width: 100%" src="leaderboard_paper.png">
</div>


</div> 

## Load the LongVideoBench Dataset


1. Download the dataset via Hugging Face CLI:

```shell
huggingface-cli download longvideobench/LongVideoBench --repo-type dataset --local-dir LongVideoBench --local-dir-use-symlinks False
```

2. Extract from the `.tar` files:

```shell
cat videos.tar.part.* > videos.tar
tar -xvf videos.tar
tar -xvf subtitles.tar
```

3. Use the [LongVideoBench] dataloader to load the data from raw MP4 files and subtitles:

- (a) Install the dataloader:

```shell
git clone https://github.com/LongVideoBench/LongVideoBench.git
cd LongVideoBench
pip install -e .
```
- (b) Load the dataset in python scripts:

```python
from longvideobench import LongVideoBenchDataset

# validation
dataset = LongVideoBenchDataset(YOUR_DATA_PATH, "lvb_val.json", max_num_frames=64)

# test
dataset = LongVideoBenchDataset(YOUR_DATA_PATH, "lvb_test_wo_gt.json", max_num_frames=64)

print(dataset[0]["inputs"]) # A list consisting of PIL.Image and strings.
```

The "inputs" are interleaved video frames and text subtitles, followed by questions and option prompts. You can then convert them to the format that your LMMs can accept.

## Evaluating with LMMs-Eval

We will integrate LongVideoBench into LMMs-Eval for inference.

## Contact

Please contact `haoning001@e.ntu.edu.sg` for any queries.

## License

This dataset follows CC-BY-NC-SA 4.0 license. Please use this dataset for non-commercial use ONLY.
