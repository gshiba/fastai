# Setup

Repos

    git clone git@github.com:gshiba/fastai.git
    git remote add upstream git@github.com:fastai/fastai.git


Environment and install

    conda deactivate  # if already activated in some other env
    conda create -n fastai
    conda actiavte fastai

    cd fastai
    tools/run-after-git-clone
    pip install -e ".[dev]"


Start coding

    git co -b new-branch
    git push


# Notes

Tutorial -- A regression example

From: `docs_src/tutorial.data.ipynb`


    data = (PointsItemList.from_folder(biwi)                         # -> vision.data.PointsItemList
            .split_by_rand_pct(seed=42)                              # -> data_block.ItemLists
            .label_from_func(lambda o:fn2ctr[o.name])                # -> data_block.LabelLists
            .transform(get_transforms(), tfm_y=True, size=(120,160)) # -> data_block.LabelLists
            .databunch()                                             # -> vision.data.ImageDataBunch
            .normalize(imagenet_stats))                              # -> vision.data.ImageDataBunch


Class hierarchy:

    object
    └─ basic_data.DataBunch
       └─ vision.data.ImageDataBunch

    object
    └─ data_block.ItemLists
       ├─ data_block.LabelLists
       ├─ data_block.ImageLists
       │  ├─ data_block.PointsItemList
       └─ vision.data.PointsLabelList
