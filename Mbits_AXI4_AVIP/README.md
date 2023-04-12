# Accelerated VIP for AXI4 Protocol

The idea of using Accelerated VIP is to push the synthesizable part of the testbench into the separate top module along with the interface and it is named as HDL TOP and the unsynthesizable part is pushed into the HVL TOP. This setup provides the ability to run the longer tests quickly. This particular testbench can be used for the simulation as well as the emulation based on mode of operation.

# Key Features  
1. Supports write and read in parallel
2. Blocking and Non Blocking Transfers
3. Separate address/control and data phases
4. Support for unaligned data transfers, using byte strobes
5. Uses burst-based transactions with only the start address issued
6. Support for issuing multiple outstanding addresses
7. Support for narrow transfers

# Architecture Diagram  
![AXI4](https://user-images.githubusercontent.com/15922511/183240262-b28b57cd-bda3-4cd8-ae2b-620d07f7a92b.jpg)

# Developers, Welcome
We believe in growing together and if you'd like to contribute, please do check out the contributing guide below:  
https://github.com/mbits-mirafra/axi4_avip/blob/phase1_development_branch/contribution_guidelines.md

# Installation - Get the VIP collateral from the GitHub repository

```
# Checking for git software, open the terminal type the command
git version

# Get the VIP collateral
git clone git@github.com:mbits-mirafra/axi4_avip.git
```

# Running the test

### Using Mentor's Questasim simulator 

```
cd axi4_avip/sim/questasim

# Compilation:  
make compile

# Simulation:
make simulate test=<test_name> uvm_verbosity=<VERBOSITY_LEVEL>

ex: make simulate test=axi4_blocking_32b_write_read_test uvm_verbosity=UVM_HIGH

# Note: You can find all the test case names in the path given below   
axi4_avip/src/hvl_top/testlists/axi4_transfers_regression.list

# Wavefrom:  
vsim -view <test_name>/waveform.wlf &

ex: vsim -view axi4_blocking_32b_write_read_test/waveform.wlf &

# Regression:
make regression testlist_name=<regression_testlist_name.list>
ex: make regression testlist_name=axi4_transfers_regression.list

# Coverage: 
 ## Individual test:
 firefox <test_name>/html_cov_report/index.html &
 ex: firefox axi4_blocking_32b_write_read_test/html_cov_report/index.html &

 ## Regression:
 firefox merged_cov_html_report/index.html &

```

### Using Cadence's Xcelium simulator 

```
cd axi4_avip/sim/cadence_sim

# Compilation:  
make compile

# Simulation:
make simulate test=<test_name> uvm_verbosity=<VERBOSITY_LEVEL>

ex: make simulate test=axi4_blocking_32b_write_read_test uvm_verbosity=UVM_HIGH

# Note: You can find all the test case names in the path given below   
axi4_avip/src/hvl_top/testlists/axi4_transfers_regression.list

# Wavefrom:  
simvision waves.shm/ &

# Regression:
make regression testlist_name=<regression_testlist_name.list>
ex: make regression testlist_name=axi4_transfers_regression.list

# Coverage:   
imc -load cov_work/scope/test/ &
```

## Technical Document 
 

## User Guide  
  

## Contact Mirafra Team  
You can reach out to us over mbits@mirafra.com

For more information regarding Mirafra Technologies please do checkout our officail website:  
https://mirafra.com/
