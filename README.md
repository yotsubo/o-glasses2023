# o-glasses2023
o-glasses2023 is an intuitive binary classification tool with machine learning.

## Requirement
* Google Colab or Jupyter Lab
* PyTorch 1.11 or later

## Dataset
We prepared our dataset for compiler identification.
When you use our dataset, decompress .zip files, and the directory structure after decompression is as follows.
```
dataset/
 +compiler_old/
 |+01_VC2003_32bit_none/
 |+02_VC2017_32bit_none/
 |+03_VC2003_32bit_max/
 |+04_VC2017_32bit_max/
 |+05_VC2017_64bit_none/
 |+06_VC2017_64bit_max/
 |+11_gcc_x86_none/
 |+12_gcc_x86_O3/
 |+13_gcc_64bit_none/
 |+14_gcc_64bit_max/
 |+21_clang_32_none/
 |+22_clang_32_O3/
 |+23_clang_64bit_none/
 |+24_clang_64bit_max/
 |+31_intel_32_none/
 |+32_intel_32bit_max/
 |+33_intel_64_none/
 |+34_intel_64bit_max/
 |+40_document
 +20200424compiler_old/
 |+01_VC2003_32bit_none/
 |+01_1_VC2003_32bit_none
 |+01_2_VC2017_32bit_none
 |+02_1_VC2003_32bit_max
 |+02_2_VC2017_32bit_max
 |+03_1_gcc6.3.0_x86_none
 |+03_2_x86-O0-gcc7.5.0
 |+04_1_gcc6.3.0_x86_O3
 |+04_2_x86-O3-gcc7.5.0
 |+05_1_clang5.0.2_32_none
 |+05_2_x86-O0-Clang10.0.0
 |+06_1_clang5.0.2_32_O3
 |+06_2_x86-O3-Clang10.0.0
 |+07_intel_32_none
 |+08_intel_32bit_max
 |+11_VC2017_64bit_none
 |+12_VC2017_64bit_max
 |+13_1_gcc6.3.0_64bit_none
 |+13_2_x86_64-O0-gcc7.5.0
 |+14_1_gcc6.3.0_64bit_max
 |+14_2_x86_64-O3-gcc7.5.0
 |+15_1_clang5.0.2_64bit_none
 |+15_2_x86_64-O0-Clang10.0.0
 |+16_1_clang5.0.2_64bit_max
 |+16_2_x86_64-O3-Clang10.0.0
 |+17_intel_64_none
 |+18_intel_64bit_max
 |+21_arm-O0-gcc
 |+22_arm-O3-gcc
 |+23_arm-O0-Clang
 |+24_arm-O3-Clang
 |+31_arm64-O0-gcc
 |+32_arm64-O3-gcc
 |+33_arm64-O0-Clang
 |+34_arm64-O3-Clang
 |+41_mips-O0-gcc
 |+42_mips-O3-gcc
 |+43_mips-O0-Clang
 |+44_mips-O3-Clang
 |+51_mips64-O0-gcc
 |+52_mips64-O3-gcc
 |+53_mips64-O0-Clang
 |+54_mips64-O3-Clang
 |+61_powerpc-O0-gcc
 |+62_powerpc-O3-gcc
 |+63_powerpc-O0-Clang
 |+64_powerpc-O3-Clang
 |+71_powerpc64-O0-gcc
 |+72_powerpc64-O3-gcc
 |+73_powerpc64-O0-Clang
 |+74_powerpc64-O3-Clang
 |+80_document

```

## Usage
### o-glasses.ipynb
This is the script used for the experiments in our paper.
To switch between experimental and learning modes, rewrite the following variables.
```
#Experimental mode = 0(Ex.1) ~ 4(Ex.5)
args_ex_mode = 0
#Learning method: 0(UTL),1(DTL),2(UFT),3(DFT),4(2LF)
args_lm = 5
```

File name of the output trained model
```
# for saving trained model
args_output_model = '20230104_01compiler'
```

Other parameters are as follows
```
#block size
op_num = 235
block_size = op_num
args_s_limit = 20000
# K-split cross-validation
args_k = 4
# num of epochs
args_epoch = 200
args_batch_size = 64
args_max_norm = 2e-1#0.25 #勾配クリッピング
args_gn_rate = 1.0 #Layer-wised Gradient Normalization

args_lr = 0.025 #Initial learning rate
args_momentum = 0.9 #Momentum
args_weight_decay = 1e-4 #Weight decay factor
args_smoothing = 0.1 #Label smoothing
```

### o-glasses_tSNE.ipynb
This is the script used to generate the image files used in Table 2 in our paper.

Replace the following variable with the filename of the trained model you wish to load.
```
args_input_model = '20230104_01compiler'
```

## Licence
Released under the MIT license
http://opensource.org/licenses/mit-license.php

## Author

[yotsubo](https://github.com/yotsubo)
