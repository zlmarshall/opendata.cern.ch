[[stripping21r1p2 lines]](./stripping21r1p2-index)

# StrippingKshort2Leptons3emuVVLine

## Properties:

|                |                                         |
|----------------|-----------------------------------------|
| OutputLocation | Phys/Kshort2Leptons3emuVVLine/Particles |
| Postscale      | 1.0000000                               |
| HLT1           | None                                    |
| HLT2           | None                                    |
| Prescale       | 1.0000000                               |
| L0DU           | None                                    |
| ODIN           | None                                    |

## Filter sequence:

LoKi::VoidFilter/StrippingGoodEventConditionLeptonic

|      |                                                                                                  |
|------|--------------------------------------------------------------------------------------------------|
| Code | ALG_EXECUTED('StrippingStreamLeptonicBadEvent') & ~ALG_PASSED('StrippingStreamLeptonicBadEvent') |

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SELECT:Phys/StdAllNoPIDsElectrons

|      |                                         |
|------|-----------------------------------------|
| Code | 0StdAllNoPIDsElectrons/Particles',True) |

FilterDesktop/Kshort2LeptonsElectronsL

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
| Code            | ( MIPCHI2DV(PRIMARY) \> 50 ) &( PT \> 100.0 ) &( TRGHOSTPROB \< 0.35 ) & ( PIDe \> -1 )       |
| Inputs          | [ 'Phys/[StdAllNoPIDsElectrons](./stripping21r1p2-commonparticles-stdallnopidselectrons)' ] |
| DecayDescriptor | None                                                                                          |
| Output          | Phys/Kshort2LeptonsElectronsL/Particles                                                       |

ChargedProtoParticleMaker/MyProtoParticlesVeloKshort2Leptons

|        |                                       |
|--------|---------------------------------------|
| Inputs | [ 'Rec/Track/Best' ]                |
| Output | Rec/ProtoP/MyProtosVeloKshort2Leptons |

NoPIDsParticleMaker/StdNoPIDsVeloElectronsKshort2Leptons

|                 |                                                     |
|-----------------|-----------------------------------------------------|
| Inputs          | [ 'Rec/ProtoP/MyProtosVeloKshort2Leptons' ]       |
| DecayDescriptor | Electron                                            |
| Output          | Phys/StdNoPIDsVeloElectronsKshort2Leptons/Particles |

FilterDesktop/Kshort2LeptonsElectronsV

|                 |                                                                                       |
|-----------------|---------------------------------------------------------------------------------------|
| Code            | ( MIPCHI2DV(PRIMARY) \> 40 ) &( PT \> 0 ) &( TRGHOSTPROB \< 0.5 ) & ( PIDe \> -1000 ) |
| Inputs          | [ 'Phys/StdNoPIDsVeloElectronsKshort2Leptons' ]                                     |
| DecayDescriptor | None                                                                                  |
| Output          | Phys/Kshort2LeptonsElectronsV/Particles                                               |

NoPIDsParticleMaker/StdNoPIDsVeloMuonsKshort2Leptons

|                 |                                                 |
|-----------------|-------------------------------------------------|
| Inputs          | [ 'Rec/ProtoP/MyProtosVeloKshort2Leptons' ]   |
| DecayDescriptor | Muon                                            |
| Output          | Phys/StdNoPIDsVeloMuonsKshort2Leptons/Particles |

FilterDesktop/Kshort2LeptonsMuonsV

|                 |                                                                                |
|-----------------|--------------------------------------------------------------------------------|
| Code            | (PT \> 50) &(MIPCHI2DV(PRIMARY) \> 10) &(TRGHOSTPROB \< 0.35) &(PIDmu \> -3.5) |
| Inputs          | [ 'Phys/StdNoPIDsVeloMuonsKshort2Leptons' ]                                  |
| DecayDescriptor | None                                                                           |
| Output          | Phys/Kshort2LeptonsMuonsV/Particles                                            |

CombineParticles/Kshort2Leptons3emuVVLine

|                  |                                                                                                                                                                                                                                    |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/Kshort2LeptonsElectronsL' , 'Phys/Kshort2LeptonsElectronsV' , 'Phys/Kshort2LeptonsMuonsV' ]                                                                                                                              |
| DaughtersCuts    | { '' : 'ALL' , 'e+' : 'ALL' , 'e-' : 'ALL' , 'mu+' : 'ALL' , 'mu-' : 'ALL' }                                                                                                                                                       |
| CombinationCut   | (AM \< 800.0 \*MeV) & (AMAXDOCA('') \< 1.0 \*mm) & ( ( ANUM( ( TRTYPE == 3 ) & ( ABSID == 'e+' ) ) == 2 ) ) & ( ( ANUM( ( TRTYPE == 1 ) & ( ABSID == 'mu+' ) ) == 1 ) ) & ( ( ANUM( ( TRTYPE == 1 ) & ( ABSID == 'e-' ) ) == 1 ) ) |
| MotherCut        | ( M \< 800.0 \*MeV) &( MIPDV(PRIMARY) \< 1 \*mm) & ( BPVVDCHI2 \> 2500) & ( VFASPF(VCHI2/VDOF) \< 35)                                                                                                                              |
| DecayDescriptor  | None                                                                                                                                                                                                                               |
| DecayDescriptors | [ '[KS0 -\> e+ e- mu+ e+]cc' , '[KS0 -\> e+ e- mu+ e-]cc' , '[KS0 -\> e+ e- mu- e+]cc' , '[KS0 -\> e+ e- mu- e-]cc' ]                                                                                                    |
| Output           | Phys/Kshort2Leptons3emuVVLine/Particles                                                                                                                                                                                            |
