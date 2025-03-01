[[stripping21 lines]](./stripping21-index)

# StrippingBs2GammaGamma_NoConvLine

## Properties:

|                |                                                      |
|----------------|------------------------------------------------------|
| OutputLocation | Phys/Bs2GammaGamma_NoConvLine/Particles              |
| Postscale      | 1.0000000                                            |
| HLT            | None                                                 |
| Prescale       | 1.0000000                                            |
| L0DU           | L0_CHANNEL_RE('Electron') \| L0_CHANNEL_RE('Photon') |
| ODIN           | None                                                 |

## Filter sequence:

CheckPV/checkPVmin1

|        |     |
|--------|-----|
| MinPVs | 1   |
| MaxPVs | -1  |

LoKi::VoidFilter/SelFilterPhys_StdLooseAllPhotons_Particles

|      |                                                                                                      |
|------|------------------------------------------------------------------------------------------------------|
| Code | CONTAINS('Phys/[StdLooseAllPhotons](./stripping21-commonparticles-stdlooseallphotons)/Particles')\>0 |

FilterDesktop/PhotonFilterBs2GammaGamma

|                 |                                                                                     |
|-----------------|-------------------------------------------------------------------------------------|
| Code            | (PT\>1250\*MeV) & (CL\>0.0)                                                         |
| Inputs          | [ 'Phys/[StdLooseAllPhotons](./stripping21-commonparticles-stdlooseallphotons)' ] |
| DecayDescriptor | None                                                                                |
| Output          | Phys/PhotonFilterBs2GammaGamma/Particles                                            |

CombineParticles/Bs2GammaGamma_none

|                  |                                                                             |
|------------------|-----------------------------------------------------------------------------|
| Inputs           | [ 'Phys/PhotonFilterBs2GammaGamma' ]                                      |
| DaughtersCuts    | { '' : 'ALL' , 'gamma' : '(PT\>1700\*MeV) & (P\>16000\*MeV) & (CL\>0.42)' } |
| CombinationCut   | (in_range(4900\*MeV, AM, 6000\*MeV))                                        |
| MotherCut        | (PT\>2000\*MeV) & (in_range(4900\*MeV, M, 6000\*MeV))                       |
| DecayDescriptor  | B_s0 -\> gamma gamma                                                        |
| DecayDescriptors | [ 'B_s0 -\> gamma gamma' ]                                                |
| Output           | Phys/Bs2GammaGamma_none/Particles                                           |

TisTosParticleTagger/Bs2GammaGamma_NoConvLine

|                 |                                            |
|-----------------|--------------------------------------------|
| Inputs          | [ 'Phys/Bs2GammaGamma_none' ]            |
| DecayDescriptor | None                                       |
| Output          | Phys/Bs2GammaGamma_NoConvLine/Particles    |
| TisTosSpecs     | { 'L0(Photon\|Electron)Decision%TOS' : 0 } |
