[[stripping21r1 lines]](./stripping21r1-index)

# StrippingButo5h_ppKpipi_exclLine

## Properties:

|                |                                        |
|----------------|----------------------------------------|
| OutputLocation | Phys/Buto5h_ppKpipi_exclLine/Particles |
| Postscale      | 1.0000000                              |
| HLT            | None                                   |
| Prescale       | 1.0000000                              |
| L0DU           | None                                   |
| ODIN           | None                                   |

## Filter sequence:

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/Buto5hGlobalEVventCutFilter

|      |                                                                |
|------|----------------------------------------------------------------|
| Code | (recSummaryTrack(LHCb.RecSummary.nLongTracks, TrLONG) \< 200 ) |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsPions_Particles

|      |                                                                                                      |
|------|------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsPions](./stripping21r1-commonparticles-stdallnopidspions)/Particles')\>0 |

LoKi::VoidFilter/SelFilterPhys_StdAllLooseProtons_Particles

|      |                                                                                                        |
|------|--------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllLooseProtons](./stripping21r1-commonparticles-stdalllooseprotons)/Particles')\>0 |

LoKi::VoidFilter/SelFilterPhys_StdAllNoPIDsKaons_Particles

|      |                                                                                                      |
|------|------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdAllNoPIDsKaons](./stripping21r1-commonparticles-stdallnopidskaons)/Particles')\>0 |

CombineParticles/Buto5h_ppKpipi_exclLine

|                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inputs           | [ 'Phys/[StdAllLooseProtons](./stripping21r1-commonparticles-stdalllooseprotons)' , 'Phys/[StdAllNoPIDsKaons](./stripping21r1-commonparticles-stdallnopidskaons)' , 'Phys/[StdAllNoPIDsPions](./stripping21r1-commonparticles-stdallnopidspions)' ]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| DaughtersCuts    | { '' : 'ALL' , 'K+' : ' (PT \> 250.0\*MeV) & (TRCHI2DOF \< 1.7) & (MIPCHI2DV(PRIMARY) \> 6.0) & (PROBNNk \> 0.2) & (TRGHP \< 0.2) ' , 'K-' : ' (PT \> 250.0\*MeV) & (TRCHI2DOF \< 1.7) & (MIPCHI2DV(PRIMARY) \> 6.0) & (PROBNNk \> 0.2) & (TRGHP \< 0.2) ' , 'p+' : ' (PT \> 250.0\*MeV) & (TRCHI2DOF \< 1.7) & (MIPCHI2DV(PRIMARY) \> 6.0) & (PROBNNp \> 0.05) & (TRGHP \< 0.2) ' , 'pi+' : ' (PT \> 250.0\*MeV) & (TRCHI2DOF \< 1.7) & (MIPCHI2DV(PRIMARY) \> 6.0) & (PROBNNpi \> 0.15) & (TRGHP \< 0.2) ' , 'pi-' : ' (PT \> 250.0\*MeV) & (TRCHI2DOF \< 1.7) & (MIPCHI2DV(PRIMARY) \> 6.0) & (PROBNNpi \> 0.15) & (TRGHP \< 0.2) ' , 'p~-' : ' (PT \> 250.0\*MeV) & (TRCHI2DOF \< 1.7) & (MIPCHI2DV(PRIMARY) \> 6.0) & (PROBNNp \> 0.05) & (TRGHP \< 0.2) ' } |
| CombinationCut   | (AM \< 5679.0\*MeV) & (AM \> 5079.0\*MeV) & (AMAXDOCA('LoKi::TrgDistanceCalculator') \< 0.14)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| MotherCut        | (BPVDIRA \> 0.99999) & (BPVVDCHI2 \> 500.0) & (VFASPF(VCHI2) \< 12.0) & (PT \> 1000.0\*MeV) & (SUMTREE(MIPCHI2DV(PRIMARY),((ABSID=='K+') \| (ABSID=='K-') \| (ABSID=='pi+') \| (ABSID=='pi-') \| (ABSID=='p+') \| (ABSID=='p~-')),0.0) \> 400.0)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| DecayDescriptor  | None                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| DecayDescriptors | [ '[B+ -\> p+ p~- K+ pi+ pi-]cc' ]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Output           | Phys/Buto5h_ppKpipi_exclLine/Particles                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
