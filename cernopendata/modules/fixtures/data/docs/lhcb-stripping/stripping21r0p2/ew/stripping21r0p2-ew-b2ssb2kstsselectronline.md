[[stripping21r0p2 lines]](./stripping21r0p2-index)

# StrippingB2SSB2KstSSElectronLine

## Properties:

|                |                                        |
|----------------|----------------------------------------|
| OutputLocation | Phys/B2SSB2KstSSElectronLine/Particles |
| Postscale      | 1.0000000                              |
| HLT1           | None                                   |
| HLT2           | None                                   |
| Prescale       | 1.0000000                              |
| L0DU           | None                                   |
| ODIN           | None                                   |

## Filter sequence:

LoKi::VoidFilter/StrippingGoodEventConditionEW

|      |                                                                                      |
|------|--------------------------------------------------------------------------------------|
| Code | ALG_EXECUTED('StrippingStreamEWBadEvent') & ~ALG_PASSED('StrippingStreamEWBadEvent') |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SELECT:Phys/StdLooseKstar2Kpi

|      |                                     |
|------|-------------------------------------|
| Code | 0StdLooseKstar2Kpi/Particles',True) |

FilterDesktop/KstarsForB2SS

|                 |                                                                                                                                                                                                                                                                            |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code            | ( PT \> 1250\*MeV)& ( MIPCHI2DV(PRIMARY)\> 55)& (PT \> 2000\*MeV )& (M \< ( 892\*MeV + 130\*MeV ) )& (M \> ( 892\*MeV - 130\*MeV ) )& (VFASPF(VCHI2/VDOF) \< 2.5 )& ( CHILD( MIPCHI2DV(PRIMARY), 1) \> 55 ) & ( CHILD( MIPCHI2DV(PRIMARY), 2) \> 55 ) & (BPVVDCHI2 \> 50 ) |
| Inputs          | [ 'Phys/[StdLooseKstar2Kpi](./stripping21r0p2-commonparticles-stdloosekstar2kpi)' ]                                                                                                                                                                                      |
| DecayDescriptor | None                                                                                                                                                                                                                                                                       |
| Output          | Phys/KstarsForB2SS/Particles                                                                                                                                                                                                                                               |

LoKi::VoidFilter/SELECT:Phys/StdAllLooseElectrons

|      |                                        |
|------|----------------------------------------|
| Code | 0StdAllLooseElectrons/Particles',True) |

FilterDesktop/ElectronsForB2SS

|                 |                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------|
| Code            | ( PT \> 25\*MeV)& ( MIPCHI2DV(PRIMARY)\> 15)                                                |
| Inputs          | [ 'Phys/[StdAllLooseElectrons](./stripping21r0p2-commonparticles-stdalllooseelectrons)' ] |
| DecayDescriptor | None                                                                                        |
| Output          | Phys/ElectronsForB2SS/Particles                                                             |

DaVinci::N5BodyDecays/B2SSB2KstSSElectronLine

|                  |                                                                                                                                                                              |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/ElectronsForB2SS' , 'Phys/KstarsForB2SS' ]                                                                                                                         |
| DaughtersCuts    | { '' : 'ALL' , 'K\*(892)0' : 'ALL' , 'K\*(892)~0' : 'ALL' , 'e+' : 'ALL' , 'e-' : 'ALL' }                                                                                    |
| CombinationCut   | (AM\>4600\*MeV) & (AM\<6000\*MeV) & (( (abs(MYAM12-MYAM34)\< 100\*MeV) \| (abs(MYAM13-MYAM24)\< 100\*MeV) \| (abs(MYAM14-MYAM23)\< 100\*MeV) ))& ((AMAXDOCA('')\< 0.3\*mm) ) |
| MotherCut        | (VFASPF(VCHI2/VDOF)\< 9)& (BPVDIRA \> 0)& (BPVVDCHI2\> 100)& (BPVIPCHI2()\< 15)                                                                                              |
| DecayDescriptor  | [B0 -\> e+ e- e+ e- K\*(892)0]cc                                                                                                                                           |
| DecayDescriptors | [ '[B0 -\> e+ e- e+ e- K\*(892)0]cc' ]                                                                                                                                   |
| Output           | Phys/B2SSB2KstSSElectronLine/Particles                                                                                                                                       |
