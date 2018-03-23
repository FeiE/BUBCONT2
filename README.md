# BUBCONT2
- [**Preprocessing**](#prepro) 

- [**Statistical analyses**](#stats) 

- [**Figures**](#fig)
     * 1D results
     * 2D results 

---

* In this experiment, the stimuli are presented through a randomly generated Bubble mask with ten Gaussian apertures on each Bubble trial. At the same time behaviour and EEG performance is recorded. 


* This project was analysed using **Matlab 2015b** and **eeglab 13.4.4b** toolbox. 

---

## <a name="prepro"></a>**Preprocessing**
[`'bubcont2_rawdata.zip'`]() contains:

  - an example of how the EEG data of one participant were pre-processed (i.g. filter, ICA, ... ).
  - the [code]() to reorganise EEG data to free up storage space.
  - the [code]() to rebuild bubble masks.
  
the **rest** of raw EEG data can be downloaded throught the [link](http://macdown.uranusjr.com "Title"). 


## <a name="stats"></a> **Statistical analyses** 
###Individual-Level

To determine the dependence between pixel intensities in bubble masks and responses of interest, we calculated Mutual Informaiton using a bin-less approach basded on Gaussian copulas. A [tutorial](http://onlinelibrary.wiley.com/doi/10.1002/hbm.23471/abstract) with [Matlab & Python code](https://github.com/robince/sensorcop) is available in Ince et al. (2016). 

---

* The figure below refers to **Framework of Whole Stimulus Sampling Analyses**.

 <img src="https://github.com/FeiE/BUBCONT2/blob/master/MI%20computation.png?raw=true" />
 
> **Centre frame**: bubble masks take values between 0 and 1, controlling the relative transparency of the mask at each pixel, with 0 being completely opaque and 1 being completely translucent. 
 
>> **Blue frame**: we can compute MI between two vectors: the distribution of behaviour performance (RT/Correct) and intensity distribution of the pixel marked in red. To obtain classification image that can reveal what information of the image is associated with responses of interest, we repeat MI calculation per each pixel within the face oval, hereafter MI(PIX, RT), MI(PIX, CORRECT). 

>>> **Orange frame**: similarly, to quantify the dependence between each pixel’s intensity from Bubble mask and bivariate responses, we compute MI(PIX, [ERP, ERP<sub>g</sub>]) at each electrode and time point, resulting in one 4D matrix (pixels x pixels x electrodes x time points).

* **Eye mask analyses**

> we summed the pixel intensitiies within left or right eye region to obtain one scalar value representing the visibility of each eye on each trial. 
 
> we then computed MI between the distribution of this scalar and corresponding responses of interest, providing new quantities: MI(EYE, RT), MI(EYE, CORRECT), MI(EYE, [ERP, ERP<sub>g</sub>])

---


### the main scripts
**`D8gcmi_beh.m`**

**`D9grad_gcmi_erp.m`**
### functions
**`gcmi_beh_bubcont2.m`**: to compute MI(**PIX**, RT), MI(**EYE**, RT), MI(**PIX**, CORRECT), MI(**EYE**, CORRECT). 

**`grad_gcmi_eye_erp_allelec_bubcont2.m`**: to compute MI(**EYE**, [ERP, ERP<sub>g</sub>]) at each electrode and time point. 

**`grad_gcmi_eye_erp_LRCelec_perm_bubcont2.m`**: to compute MI(**EYE**, [ERP, ERP<sub>g</sub>]) at each posterior lateral electrode of interest and time point. permutation test is applied to find statistical significance. 

**`topography.m`**: to obtain topographic map.

**`maxmi_perframe_acrLRCeles.m`**:

**`grad_gcmi_eye_erp_onset_bubcont2.m`**: to determine the onset of 



**`grad_gcmi_pix_erp_LRCelecframe_bubcont2.m`**

**`grad_gcmi_pix_erp_PLelecframe_bubcont2.m`**

**`maxmi_perframe_acrPLeles.m`**

### Group-Level<sub>*Figures* 
<a name="fig"></a>Figures
