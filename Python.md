## activate virtual environment

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



### Install python package in my macbook

````
/opt/homebrew/bin/python3.11 -m pip install seaborn
/opt/homebrew/bin/python3.11 -m pip install intake-esm
/opt/homebrew/bin/python3.11 -m pip install requests
/opt/homebrew/bin/python3.11 -m pip install aiohttp
/opt/homebrew/bin/python3.11 -m pip install gcsfs
/opt/homebrew/bin/python3.11 -m pip install climetlab
/opt/homebrew/bin/python3.11 -m pip install zarr
/opt/homebrew/bin/python3.11 -m pip install dask

/usr/bin/python3 -m pip install seaborn
/usr/bin/python3 -m pip install --upgrade xarray

/opt/homebrew/bin/python3.11 -m pip install xarray
/opt/homebrew/bin/python3.11 -m pip install netcdf4 scipy rasterio

/usr/bin/python3 -m pip install statsmodels
````



# Python package

## 1 xarray

- 常用于读取netcdf文件

````
import xarrary as xr
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



### matplotlib

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

## 4 scipy.stats

### **t-test**:

https://mp.weixin.qq.com/s/jBgRM_pvMEuZ2-1NqpoePw



## Read in a number of nc.files