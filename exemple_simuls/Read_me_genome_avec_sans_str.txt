##### Code pour la simulation d'un coalescent sans structure

nb.genos <- 500 # nombre de génotypes
nb.chroms <- 5
Ne <- 10^4 # taille efficace
chrom.len <- 5*10^5 # longueur de chaque chromosome
mu <- 10^(-8) # taux de mutation
c.rec <- 10^(-8) # taux de recombinaison

genomes <- simulCoalescent(nb.inds=nb.genos, nb.reps=nb.chroms,
                           pop.mut.rate=4 * Ne * mu * chrom.len,
                           pop.recomb.rate=4 * Ne * c.rec * chrom.len,
                           chrom.len=chrom.len,
                           #mig.rate=5, # => valeur par défaut sans structure
                           nb.pops=1, 
                           verbose=1)

##### Code pour la simulation d'un coalescent avec structure

mig.rates <- 0.1*4*Ne # faible migration => forte structure
# autres valeurs possibles à tester pour mig.rates : 0.4 / 0.7 / 1.2
nb.pops <- 10 # nombre de populations (+/- différenciées)
chrom.len <- 10^4
nb.genos2 <- 300
genomes.struct <- simulCoalescent(nb.inds=nb.genos2,
                                  nb.reps=nb.chroms,
                                  pop.mut.rate=4 * Ne * mu * chrom.len,
                                  pop.recomb.rate=4 * Ne * c.rec * chrom.len,
                                  chrom.len=chrom.len,
                                  nb.pops=nb.pops,
                                  mig.rate=mig.rates,
                                  verbose=1)

### Changer le path to file
load("genome_avec_str.RData")
load("genome_sans_str.RData")