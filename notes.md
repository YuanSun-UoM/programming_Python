## 1 activate a virtual environment

- use conda to manage package

````
# creat a new environment
conda create --name myenv python=3.11 # specify the Python version you want to use

# remove a conda environment
conda env remove -n myenv

# check conda version
conda --version

# check conda installation directory
conda info --base

# check existing conda environment 
conda env list

# Activate the environment
conda activate myenv

# install package
conda install -n myenv numpy pandas xarray matplotlib zarr gcsfs cftime nc-time-axis climetlab cdsapi

# check if numpy is exsiting within the environment
conda list -n myenv | grep numpy

# generate 'environment.yml' from an existing conda
conda activate myenv
conda env export > environment.yml
````



### 1.1 Install python package in my macbook

````
/opt/homebrew/bin/python3.11 -m pip install seaborn
/opt/homebrew/bin/python3.11 -m pip install intake-esm
/opt/homebrew/bin/python3.11 -m pip install requests
/opt/homebrew/bin/python3.11 -m pip install aiohttp
/opt/homebrew/bin/python3.11 -m pip install gcsfs
/opt/homebrew/bin/python3.11 -m pip install climetlab
/opt/homebrew/bin/python3.11 -m pip install zarr
/opt/homebrew/bin/python3.11 -m pip install dask
/opt/homebrew/bin/python3.11 -m pip install xarray
/opt/homebrew/bin/python3.11 -m pip install netcdf4 scipy rasterio

/usr/bin/python3 -m pip install seaborn
/usr/bin/python3 -m pip install --upgrade xarray
/usr/bin/python3 -m pip install statsmodels
````

### 1.2 install packages used in an existing virtual environment

```
# archer2 
cd /work/n02/n02/yuansun/
module load cray-python
source /work/n02/n02/yuansun/myvenv/bin/activate
pip freeze > myvenv_requirements.txt

# 创建环境后，安装已有环境中的包
pip install -r myvenv_requirements.txt

# numpy 和某个版本冲突，还是逐个安装吧
rm -rf myvenv
```

### Error
**Error1**:

(my_virtual_env) [yuan1239@cylc1 yuansun]$ pip install -r /gws/nopw/j04/duicv/yuansun/myvenv_requirements.txt
Processing /home/jenkins/rpmbuild/BUILD/cray-python-3.9.13.1-202207292200_5a2fb49/nose-1.3.7-py3-none-any.whl (from -r /gws/nopw/j04/duicv/yuansun/myvenv_requirements.txt (line 108))
ERROR: Could not install packages due to an OSError: [Errno 2] No such file or directory: '/home/jenkins/rpmbuild/BUILD/cray-python-3.9.13.1-202207292200_5a2fb49/nose-1.3.7-py3-none-any.whl'

**solved** : deleted this package

**Error2**:

ERROR: Ignored the following yanked versions: 8.1.0
ERROR: Ignored the following versions that require a different python version: 1.21.2 Requires-Python >=3.7,<3.11; 1.21.3 Requires-Python >=3.7,<3.11; 1.21.4 Requires-Python >=3.7,<3.11; 1.21.5 Requires-Python >=3.7,<3.11; 1.21.6 Requires-Python >=3.7,<3.11; 2023.3.2 Requires-Python <3.11,>=3.8; 2023.5.0 Requires-Python <3.11,>=3.8; 2023.6.0 Requires-Python <3.11,>=3.8; 2023.6.0 Requires-Python <=3.11,>=3.9; 2023.7.0 Requires-Python <3.11,>=3.8; 2023.9.0 Requires-Python <3.11,>=3.8
ERROR: Could not find a version that satisfies the requirement pytest==0.0.0 (from versions: 2.0.0, 2.0.1, 2.0.2, 2.0.3, 2.1.0, 2.1.1, 2.1.2, 2.1.3, 2.2.0, 2.2.1, 2.2.2, 2.2.3, 2.2.4, 2.3.0, 2.3.1, 2.3.2, 2.3.3, 2.3.4, 2.3.5, 2.4.0, 2.4.1, 2.4.2, 2.5.0, 2.5.1, 2.5.2, 2.6.0, 2.6.1, 2.6.2, 2.6.3, 2.6.4, 2.7.0, 2.7.1, 2.7.2, 2.7.3, 2.8.0, 2.8.1, 2.8.2, 2.8.3, 2.8.4, 2.8.5, 2.8.6, 2.8.7, 2.9.0, 2.9.1, 2.9.2, 3.0.0, 3.0.1, 3.0.2, 3.0.3, 3.0.4, 3.0.5, 3.0.6, 3.0.7, 3.1.0, 3.1.1, 3.1.2, 3.1.3, 3.2.0, 3.2.1, 3.2.2, 3.2.3, 3.2.4, 3.2.5, 3.3.0, 3.3.1, 3.3.2, 3.4.0, 3.4.1, 3.4.2, 3.5.0, 3.5.1, 3.6.0, 3.6.1, 3.6.2, 3.6.3, 3.6.4, 3.7.0, 3.7.1, 3.7.2, 3.7.3, 3.7.4, 3.8.0, 3.8.1, 3.8.2, 3.9.1, 3.9.2, 3.9.3, 3.10.0, 3.10.1, 4.0.0, 4.0.1, 4.0.2, 4.1.0, 4.1.1, 4.2.0, 4.2.1, 4.3.0, 4.3.1, 4.4.0, 4.4.1, 4.4.2, 4.5.0, 4.6.0, 4.6.1, 4.6.2, 4.6.3, 4.6.4, 4.6.5, 4.6.6, 4.6.7, 4.6.8, 4.6.9, 4.6.10, 4.6.11, 5.0.0, 5.0.1, 5.1.0, 5.1.1, 5.1.2, 5.1.3, 5.2.0, 5.2.1, 5.2.2, 5.2.3, 5.2.4, 5.3.0, 5.3.1, 5.3.2, 5.3.3, 5.3.4, 5.3.5, 5.4.0, 5.4.1, 5.4.2, 5.4.3, 6.0.0rc1, 6.0.0, 6.0.1, 6.0.2, 6.1.0, 6.1.1, 6.1.2, 6.2.0, 6.2.1, 6.2.2, 6.2.3, 6.2.4, 6.2.5, 7.0.0rc1, 7.0.0, 7.0.1, 7.1.0, 7.1.1, 7.1.2, 7.1.3, 7.2.0, 7.2.1, 7.2.2, 7.3.0, 7.3.1, 7.3.2, 7.4.0, 7.4.1, 7.4.2, 7.4.3, 7.4.4, 8.0.0rc1, 8.0.0rc2, 8.0.0, 8.0.1, 8.0.2, 8.1.1, 8.1.2, 8.2.0, 8.2.1, 8.2.2, 8.3.0, 8.3.1, 8.3.2, 8.3.3)
ERROR: No matching distribution found for pytest==0.0.0

**solved**: change to pytest==8.3.3 and pluggy==1.5.0。 pytest 8.3.3 depends on pluggy<2 and >=1.5



**Error3**:

      In file included from src/MPI.c:4:
      src/mpi4py.MPI.c:198:12: fatal error: longintrepr.h: No such file or directory
        198 |   #include "longintrepr.h"
            |            ^~~~~~~~~~~~~~~
      compilation terminated.
      error: command '/apps/jasmin/jaspy/miniforge_envs/jaspy3.11/mf3-23.11.0-0/envs/jaspy3.11-mf3-23.11.0-0-v20240815/bin/mpicc' failed with exit code 1
      [end of output]

  note: This error originates from a subprocess, and is likely not a problem with pip.
  ERROR: Failed building wheel for mpi4py

**note**: this error occurs due to Python3.11 do not have longintrepr.h 文件[ref](https://stackoverflow.com/questions/74979674/gensim-install-in-python-3-11-fails-because-of-missing-longintrepr-h-file), update mpi4py version



**Error4**: when import xarray as xr

ImportError: numpy.core.multiarray failed to import



**Error5**:

/gws/nopw/j04/duicv/yuansun/my_virtual_env/lib/python3.11/site-packages/xarray/backends/plugins.py:80: RuntimeWarning: Engine 'rasterio' loading failed:

'TlzSpec' object has no attribute '_uninitialized_submodules'

 warnings.warn(f"Engine {name!r} loading failed:\n{ex}", RuntimeWarning)

**solved**: pip install --upgrade xarray rasterio



# Python package

## 1 xarray

- 常用于读取netcdf文件

````
import xarray as xr
````



## 2 numpy

```text
import numpy as np
```



### np.mean()

- summary statistics

````
numpy.mean(a, axis, dtype)

# 假设a为[time, lat, lon]
axis    ：  不设置值，对 time,lat, lon 个值求均值，返回一个数
axis = 0：压缩时间维，对每一个经纬点求均值，返回 [lat, lon] 数组(如求一个场的N年气候态)
axis =1,2 ：压经度纬度，对每个时间求平均值，返回 [time] 矩阵(如求某时间序列，或指数)
````



### np.std()

### Nan

- Nan grid的加减不会进行，还是nan;



## 3 pandas



## 4 matplotlib

```
import matplotlib.pyplot as plt
```

```
plt.savefig('hete_space.png',dpi=300) 
plt.savefig('hete_space.pdf',dpi=600) 
# 如果同时导出，则需在同一个命令行中，否则导出的pdf是空白的
# 或者应该调用fig
fig, axs = plt.subplots(3, 3, figsize=(7, 4), subplot_kw={'projection': proj}, gridspec_kw={'hspace': 0.2, 'wspace': 0.2})
fig.savefig('hete_space.pdf',dpi=600) 
```

- 使用proj = ccrs.PlateCarree(central_longitude=180) 时，地图的横坐标最两端都有0°的label。 如果用proj = ccrs.PlateCarree()，最右端没有0°的label。

## 5 scipy.stats

### **t-test**

- https://mp.weixin.qq.com/s/jBgRM_pvMEuZ2-1NqpoePw