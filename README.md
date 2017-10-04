The dual rich analyzer is a C++ code in which the Indirect Ray Tracing (see [1,2]) algorithm has been implemented. A small update of the alghorithm has been added with respect to the original one; nemely, if applyed to a dual-radiator RICH, the refraction of the light at the radiators interfaces is taken into account knowing the indexes of refraction of the materials. 

Mother class: eic_dual_rich 

Implemented methos:

set_mirror(Double_t center_posx, Double_t center_posy, Double_t center_posz, Double_t radius) //set the mirror parameters
set_radiator_one(Double_t mean_refraction_index1) //set index of refraction of the first radiator
set_radiator_two(Double_t mean_refraction_index2) //set index of refraction of the second radiator
ind_ray(Double_t Ex, Double_t Ey, Double_t Ez, Double_t Dx, Double_t Dy, Double_t Dz, Double_t vx, Double_t vy, Double_t vz, Int_t select_radiator) //Indirect Ray Tracing:

Ex,Ey,Ez are the coordinates of the emission point of the cherenkov photon (usually unknown, the middle point of a track in the radiator can be assumed as emission point),
Dx,Dy,Dz are the coordinates of the hit of the photon in the detector surface
vx,vy,vz are the coordinates of the versor of the emitting track
select_radiator is an optional selection lable: if 1 the first radiator in a dual-radiator configuration is slected (the refraction correction is applied), in the default configuration the single radiator mode is selected (select_radiator!=1)

fill_cherenkov_array(Double_t angle) //fill the cherenkov angle array (vector<Double_t> ch_vector)
cut_cherenkov_array(Double_t theta_min, Double_t theta_max) //apply cuts to the cherenkov angles on ch_vector 
mean_cherenkov_angle() //mean value on ch_vector
SD_cherenkov_angle() //SD on ch_vector
clear_cherenkov_array()//clear ch_vector

////////Compilation and usage in ROOT/////////
//.L dualrich_analyzer.cpp++
//eic_dual_rich *a = new eic_dual_rich()
//a->some method of the class


[1] Akopov, N., et al. "The HERMES dual-radiator ring imaging Cherenkov detector." Nuclear Instruments and Methods in Physics Research Section A: Accelerators, Spectrometers, Detectors and Associated Equipment 479.2 (2002): 511-530.

[2] E. Cisbani et al., HERMES internal note 97-003(1997)
