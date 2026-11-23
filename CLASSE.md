# Seguiment de la classe

## Llindar de sonoritat

La funció `unvoiced()` mira `rmaxnorm`, que és l’autocorrelació del candidat de pitch dividida per `r[0]`. Si supera el llindar, retornem `false`: el bloc es considera sonor. Si no el supera, retornem `true` i el pitch de sortida és zero.

Hem compilat amb `make release` i hem passat les 50 gravacions amb `run_get_pitch`.

| Llindar | Sord classificat com a sonor | Sonor classificat com a sord | Errors grossos de pitch | TOTAL |
|---|---:|---:|---:|---:|
| 0,5 | 5,71 % | 17,04 % | 0,75 % | **87,21 %** |
| 0,6 | 2,85 % | 28,83 % | 0,41 % | **84,09 %** |

El 0,5 reprodueix el resultat que es veu a la captura de classe. Amb 0,6 demanem una correlació més alta: marquem menys soroll com a sonor, però perdem més veu sonora. Per això baixa el TOTAL, tot i que baixen alguns errors.

El codi es queda a **0,6**, com es veu a la captura de l’editor. El 0,5 s’ha provat en una còpia temporal, sense canviar la branca. Els `.f0` de `pitch_db/train` corresponen al codi actual amb 0,6.

Els resums són a [classe_llindar_0.5.txt](resultats/classe_llindar_0.5.txt) i [classe_llindar_0.6.txt](resultats/classe_llindar_0.6.txt).

Aquesta és una primera comparació, no la configuració final de la pràctica. Encara falten les gràfiques, la comparació amb WaveSurfer i la resta de proves.
