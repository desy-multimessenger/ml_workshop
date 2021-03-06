# ml_workshop

We now use this for the first stage of classification for the ELAsTiCC challenge.

Useful links:
- [ELAsTiCC documentation](https://portal.nersc.gov/cfs/lsst/DESC_TD_PUBLIC/ELASTICC/)
- [Data](https://syncandshare.desy.de/index.php/s/LLzErE9QgLpNFLZ)

How To:
```python
import os, logging
from train_models import Model

logging.basicConfig()
logger = logging.getLogger()
logger.setLevel(logging.INFO)

path_to_trainingset = os.path.join(
    os.path.dirname(os.path.realpath(__file__)),
    "data",
    "elasticc_feature_trainingset_v3",
)

m = Model(
    stage="1",
    path_to_trainingset=path_to_trainingset,
    n_iter=10,
    random_state=42,
    one_alert_per_stock=True,
)
m.split_sample()
m.train()
m.evaluate()
```