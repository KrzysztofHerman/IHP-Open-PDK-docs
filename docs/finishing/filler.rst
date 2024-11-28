
Filler generation using KLAYOUT
================================

.. _filler_generation_lbl:


The filling process can be run from the command line using either provided python script:

.. code-block:: bash
    
  klayout -n sg13g2 -zz -r $PDK_ROOT/$PDK/libs.tech/klayout/tech/scripts/filler.py -rd output_file=./design_filled.gds design_nofill.gds   

or using items in the ``SG13G2 PDK`` menu items. 

It is mandatory to have a ``sealring`` in the design which can be dragged and dropped from the ``libraries`` menu in klayout left pane. 

In the actual version in order to control metal filler densities user can modify the following scripts:

.. code-block:: bash
 
  $PDK_ROOT/$PDK/libs.tech/klayout/tech/scripts/macros/sg13g2_filler_Metal.lym  
  $PDK_ROOT/$PDK/libs.tech/klayout/tech/scripts/macros/sg13g2_filler_TopMetal.lym

where the ``width``, ``length`` and also the ``distance`` between the filler cells can be modified in order to reach a desired density level.  Please respect 
the DRC rules related to the sizes and separation of the filler cells (sections ``5.18`` and ``5.23`` of the ``SG13G2_Layout_Rules_os.pdf`` document). 

After running the fillers one can check if the desired density level is met by using Density Report from the ``SG13G2 PDK`` menu. 

While running ``minimal DRC`` in klayout one can expect ``AFil.g2``, ``M1-5Fil.h``  errors related to the area outside the design, where the densities are calculated. The errors can be waived. 

