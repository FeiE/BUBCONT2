# BUBCONT2
- [**Preprocessing**](#prepro) 

- [**Analyses Framework**](#stats) 
   - [MI Scripts](#mi)
   - [Figures Scripts](#fig)

---

* In this experiment, the stimulus was presented through a randomly generated Bubble mask with ten Gaussian apertures on each Bubble trial. At the same time behaviour and EEG performance were recorded. 

* This project was analysed using **Matlab 2015b**, **eeglab 13.4.4b**, **LIMO** toolbox. 

* we uploaded three split folders ([**`bubcont2_rawdata`**]() & [**`bubcont2_prepro`**]() & [**`bubcont2_analyses`**]()), separately involving raw EEG data, pre-processing and the following analyses. 

***NOTE***: Run **`runmefirst.m`** first to set path. Then run the main scripts with the name starting with number. 

---

## <a name="prepro"></a>**Preprocessing**
**`bubcont2_prepro`**[(link)]() contains:

  - an example of how the EEG data of one participant were pre-processed (i.g. filter, ICA, CSD ).
    - **`1prepro_preica_bubcont2.m`**
    - **`2prepro_ica_bubcont2.m`**
    - **`3prepro_postica_bubcont2.m`**
  - **`4bubblemasks_rebuild_bubcont2.m`**: to reorganise EEG data to free up storage space.
  - **`5make_dat_bubcont2.m`**: to rebuild bubble masks.
  - **`6n170_elec_selection.m`**: to select the electrode showing minimum voltage across self defined time course and electrodes of interest, and to save corresponding details of this electrode. 
  
the **rest** of raw EEG data can be found in **`bubcont2_rawdata`**[(link)](). 


## <a name="stats"></a> **Analyses Framework** 
---

To determine the dependence between pixel intensities in bubble masks and responses of interest, we calculated Mutual Informaiton（MI）using a bin-less approach basded on Gaussian copulas. A [tutorial](http://onlinelibrary.wiley.com/doi/10.1002/hbm.23471/abstract) with [Matlab & Python code](https://github.com/robince/sensorcop) is available in Ince et al. (2016). 

---

* The figure below corresponds to *Whole Stimulus Sampling Analyses*.

 <img src="https://github.com/FeiE/BUBCONT2/blob/master/MI%20computation.png?raw=true" width = 450/>
 
> **Centre frame**: bubble masks take values between 0 and 1, controlling the relative transparency of the mask at each pixel, with 0 being completely opaque and 1 being completely translucent. 
>     
>> **Blue frame**: we can compute MI between two vectors: the distribution of behaviour performance (RT/Correct) and intensity distribution of the pixel marked in red. To obtain classification image that can reveal what information of the image is associated with responses of interest, we repeat MI calculation per each pixel within the face oval, hereafter MI(PIX, RT), MI(PIX, CORRECT). 
>> 
>>> **Orange frame**: similarly, to quantify the dependence between each pixel’s intensity from Bubble mask and bivariate responses, we compute MI(PIX, [ERP, ERP<sub>g</sub>]) at each electrode and time point, resulting in one 4D matrix (pixels x pixels x electrodes x time points).


* *Eye mask analyses*

> we summed the pixel intensitiies within left or right eye region to obtain one scalar value representing the visibility of each eye on each trial. 
> 
> we then computed MI between the distribution of this scalar and corresponding responses of interest, providing new quantities: MI(EYE, RT), MI(EYE, CORRECT), MI(EYE, [ERP, ERP<sub>g</sub>])

---

### <a name="mi"></a>MI Scripts

**`7gcmi_beh.m`**

> `gcmi_beh_bubcont2.m`: to compute MI(**PIX**, RT), MI(**EYE**, RT), MI(**PIX**, CORRECT), MI(**EYE**, CORRECT). 

**`8grad_gcmi_erp.m`**
> *Whole Stimulus Sampling Analyses*
>>
>> `grad_gcmi_pix_erp_LRCelecframe_bubcont2.m`: to compute MI(**PIX**, [ERP, ERP<sub>g</sub>]) at each posterior lateral electrode（<img src="https://github.com/FeiE/BUBCONT2/blob/master/LE.png?raw=true" width = 30/> & <img src="https://github.com/FeiE/BUBCONT2/blob/master/RE.png?raw=true" width = 30/>) and time point.
>>
>> `grad_gcmi_pix_erp_Pelecframe_bubcont2.m`: to compute MI(**PIX**, [ERP, ERP<sub>g</sub>]) at each posterior electrode <img src="https://github.com/FeiE/BUBCONT2/blob/master/PL.png?raw=true" width = 30/> and time point.
>>
>> `maxmi_perframe_acrPeles.m`: to get the maximum MI(**PIX**, [ERP, ERP<sub>g</sub>]) across posterior electrodes <img src="https://github.com/FeiE/BUBCONT2/blob/master/PL.png?raw=true" width = 30/>. 
>
>
> *Eye Mask Analyses*
>>
>>`grad_gcmi_eye_erp_allelec_bubcont2.m`: to compute MI(**EYE**, [ERP, ERP<sub>g</sub>]) at every electrodes and time points. 
>>
>> `topography.m`: to obtain topographic map of MI(**EYE**, [ERP, ERP<sub>g</sub>]).
>>
>> `grad_gcmi_eye_erp_LRCelec_perm_bubcont2.m`: to compute MI(**EYE**, [ERP, ERP<sub>g</sub>]) at each posterior lateral electrode of interest（<img src="https://github.com/FeiE/BUBCONT2/blob/master/LE.png?raw=true" width = 30/> & <img src="https://github.com/FeiE/BUBCONT2/blob/master/RE.png?raw=true" width = 30/>）and time point. permutation test is applied to find statistical significance. 
>>
>> `maxmi_perframe_acrLRCeles.m`: to get the maximum MI(**EYE**, [ERP, ERP<sub>g</sub>]) across posterior lateral electrode of interest（<img src="https://github.com/FeiE/BUBCONT2/blob/master/LE.png?raw=true" width = 30/> & <img src="https://github.com/FeiE/BUBCONT2/blob/master/RE.png?raw=true" width = 30/>.
>>
>> `grad_gcmi_eye_erp_onset_bubcont2.m`: to determine the onset of MI(**EYE**, [ERP, ERP<sub>g</sub>])  


### <a name="fig"></a>Figures Scripts

**`9n170_measure_fig.m`**
> `waveform_erpdiff_bubcount2.m`
> 
> <img src="https://github.com/FeiE/BUBCONT2/blob/master/waveform_erpdiff_bubcount2.png?raw=true" width = 300/>
> 
**`10gcmi_beh_fig.m`**
>
> `ClassificationImage.m`
>>  <img src="https://github.com/FeiE/BUBCONT2/blob/master/ClassificationImage.png?raw=true" width = 100/>
>
> `scatterplot_single_subj.m`
> 
>>  <img src="https://github.com/FeiE/BUBCONT2/blob/master/scatterplot_single_subj.png?raw=true" width = 500/>
>
> `diff_matrix_bubcont2_bin.m`
>
>>  <img src="https://github.com/FeiE/BUBCONT2/blob/master/diff_matrix_bubcont2_bin.png?raw=true" width = 350/>
>


**`11grad_gcmi_erp_fig.m`**
> `scatterplot_diff.m`
>>  <img src="https://github.com/FeiE/BUBCONT2/blob/master/scatterplot_diff.png?raw=true" width = 200/>
>
> `waveform_diff_bubcont2.m`:
>>  <img src="https://github.com/FeiE/BUBCONT2/blob/master/waveform_diff_bubcont2.png?raw=true" width = 400/>
>
> `waveform_diff_bubcont2_single.m`
>
>>  <img src="https://github.com/FeiE/BUBCONT2/blob/master/waveform_diff_bubcont2_single.png?raw=true" width = 400/>
> 
> `waveform_bubcont2_single.m`
>
>>  <img src="https://github.com/FeiE/BUBCONT2/blob/master/waveform_bubcont2_single.png?raw=true" width = 400/>
>
> `waveform_diff_bubcont2_onset.m`
> 
>>  <img src="https://github.com/FeiE/BUBCONT2/blob/master/waveform_diff_bubcont2_onset.png?raw=true" width = 400/>
>
> `topography_fig.m`
> 
>>  <img src="https://github.com/FeiE/BUBCONT2/blob/master/togography.png?raw=true" width = 100/>
