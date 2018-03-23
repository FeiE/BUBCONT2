# BUBCONT2
- [**Preprocessing**](#prepro) 

- [**Statistical analyses**](#stats) 
  * [behaviour](#beh) 
     * [MI calculation](#mibeh)
     * [Figures](#behfig)
         * 1D results
         * 2D results 
  * [brain activity](#brain) 
     * [N170](#n170)
     * [MI calculation (*ERP, ERP<sub>g</sub>*)](#mierp)
     * [Figures](#erpfig)
         * 1D results
         * 2D results 

---

This project was processed using Matlab 2015b and eeglab 13.4.4b toolbox. 

---

## <a name="prepro"></a>**Preprocessing**
[`'bubcont2_rawdata.zip'`]() contains:

  - an example of how the EEG data of one participant were pre-processed (i.g. filter, ICA, ... ).
  - the [code]() to reorganise EEG data to free up storage space.
  - the [code]() to rebuild bubble masks.
  
the **rest** of raw EEG data can be downloaded throught the [link](http://macdown.uranusjr.com "Title"). 


## <a name="stats"></a>**Statistical analyses**

 * to determine the dependence between pixel intensities in bubble masks and responses of interest, we calculated Mutual Informaiton using a bin-less approach basded on Gaussian copulas. A [tutorial](http://onlinelibrary.wiley.com/doi/10.1002/hbm.23471/abstract) with [Matlab & Python code](https://github.com/robince/sensorcop) is available in Ince et al. (2016). 
 * MI calculation is 


### <a name="beh"></a> **behaviour**
<a name="mibeh"></a><u>MI calculation</u> 


<a name="behfig"></a><u>Figures</u> 

### <a name="brain"></a> **brain activity**
<a name="n170"></a><u>N170</u> 

<a name="mierp"></a><u>MI calculation</u> 


<a name="erpfig"></a><u>Figures</u> 
