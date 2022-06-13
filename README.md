# Dataset4EO
# RSI-Segmentation
<div  align="center">    
 <img src="resources/datasets4eo.png" width = "400" height = "150" alt="segmentation" align=center />
</div>

![example workflow](https://github.com/github/docs/actions/workflows/main.yml/badge.svg)

Todo List

- [x] Re-organize mroe than 180 datasets in Remote sensing cimmunity in a task-oriented way;
- [x] Assign specific datasets to each of the member;
- [ ] preprocess the datasets in a AI-ready style;
- [ ] re-distribute processed datasets and add citations;
- [ ] implementing dataset classes for downloading;
- [ ] implementing the random sampler for geo-spatial datasets;
- [ ] supporting for heigh-level repos for specific tasks: obejct detection, segmentation and so forth;
- [ ] supporting dataloaders in a easy-to-use way for custom projects;
- [ ] benchmarking all the cutting-edge backbones and task-specific models;


## How to use

### Install newest versions of torch and torchdata
```shell
sh install_requirements.sh
python -m pip install -e .
```

### Install Dataset4EO
```shell
python -m pip install -e .
```

### Then it can be used by
```python
from Dataset4EO.datasets import list_datasets, load, landslide4sense
from torch.utils.data import DataLoader2
from tqdm import tqdm

#list all the supported datasets
print(list_datasets())

#create new dataset object by calling:
datasets_dir = './'
dp = landslide4sense.Landslide4Sense(datasets_dir, split='train')

#create a dataloader by calling:
data_loader = DataLoader2(dp.shuffle(), batch_size=4, num_workers=4, shuffle=True, drop_last=True)

#Now, iterating the dataloader for training
for it in tqdm(data_loader):
    print(it)
```

# Add Transformations
```python
from Dataset4EO import transforms

tfs = transforms.Compose(transforms.RandomHorizontalFlip(),
                                 transforms.RandomVerticalFlip(),
                                 transforms.RandomResizedCrop((128, 128), scale=[0.5, 1]))
                                 
ndp = ndp.map(tfs)
```
