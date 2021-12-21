For installation of the DeePMD-kit package, please refer to https://github.com/deepmodeling/deepmd-kit

                                        WORKFLOW

==============stage 1 dp training=============== 

Version:    deepmd-kit 1.3.3
Input file:    gra_sm.json
Command:    dp train gra_sm.json
Output file:    frozen_model.pb

==============stage 2 dp compress==============

Version:   deepmd-kit 2.0.3
Input file:    frozen_model.pb； gra_sm_new.json
Command:    dp convert-from 1.3 -i frozen_model.pb -o frozen_model_new.pb
	     dp compress -i frozen_model_new.pb -o frozen_model_compress.pb --training-script gra_sm_new.json
Output file:   frozen_model_compress.pb

==============stage 3 DPMD==================

Version:    deepmd-kit 2.0.3
Input file:    in.lammps； frozen_model_compress.pb 
Command:    lmp -in in.lammps


If you don't want to take time to train your own DP, you can simply jump tp "stage 3" to run DPMD simulations on systems of interest，with the DP provided.