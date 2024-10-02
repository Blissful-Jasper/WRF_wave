## WRF  with intel

河海大学-海洋学院集群WRF修改源代码后的重新编译的参数配置

./clean -a

./configure



首先选择：15 并行计算

然后选择：basic=1的网格

./compile em_real 



```bash



## NETCDF

export NETCDF=/usr/local/NetCDF471_f44
export PATH=$NETCDF/bin:$PATH
export LD_LIBRARY_PATH=$NETCDF/lib:$LD_LIBRARY_PATH

## MPI

export MPI=/usr/local/mpich3.3.2
export PATH=$MPI/bin:$PATH
export LD_LIBRARY_PATH=$MPI/lib:$LD_LIBRARY_PATH

## JASPER

export JASPERLIB=/usr/local/jasper1.900.1/lib
export JASPERINC=/usr/local/jasper1.900.1/include

## libpng  解决找不到libpng.12.so.0的问题

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/gpfs/tfeng/xpji/Library/libpng_1.2.12/lib/


## WRF

export CC=icc
export CXX=icpc
export CFLAGS='-O3 -xHost -ip -no-prec-div -static-intel'
export CXXFLAGS='-O3 -xHost -ip -no-prec-div -static-intel'
export F77=ifort
export FC=ifort
export F90=ifort
export FFLAGS='-O3 -xHost -ip -no-prec-div -static-intel'
export CPP='icc -E'
export CXXCPP='icpc -E'

export WRFIO_NCD_LARGE_FILE_SUPPORT=1
ulimit -s unlimited
```

记得source ~/.bashrc





修改了/gpfs/tfeng/xpji/WRFV3/dyn_em/module_em.F 中的计算辐射的公式



/gpfs/tfeng/xpji/WRFV3/