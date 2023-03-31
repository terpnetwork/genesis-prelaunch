# Distribution:
## Determination of percentiles
The process of finding a fair airdrop method is based on WyndDAOs decentralized airdrop process, which uses percentiles and normalization for each projects token holder map statistics included via consensus of various TestNET DAOs and subDAOs. This process involves the following steps:

Percentiles are calculated for each project based on how many holders there are, and the distribution of supply between those holders. If you are a holder of a project with X amount of tokens, then your X amount ownership would fall into one of the ownership percentile ranges.

## Normalization
For each defi community holder distribution calculated, a tier system was needed for allocating a set number of points for holders who land in each percentile range.

**Calculations:**
 We use piecewise linear curves for all items, constant above a minimum and maximum. Given user $X$ is percentile $\rho$ in some metric (balance), we define the reward formula as:
```
Reward(R)= func(p, a, b, min, max)

    =a ; if p < min
    =b ; if p > max 
    =a + ((b-a) * (p-min)/(max-min)) ; otherwise 
```
Where a,b are for percentile cutoffs over a range of points in terms of min,max.


## Minting Schedule
### TERP
No minting or inflation schedule set.
### PERSY 
93% first year, 1/3rd less each following year (Model based off of Osmosis Zones Thirdening Schedule)
| year 0  |  420,000,000  | 93.00% | 390,600,000 |   |
|---------|:----------------:|:------:|:-----------:|---|
| year 1  | 810,600,000 | 62.00%   | 502,572,000    |   |
| year 2  | 1,313,172,000 | 41.33% | 542,777,760.00 |   | 
| year 3  | 1,855,949,760 | 27.56% | 511,417,267.20 |   |
| year 4  | 2,367,367,027| 18.37%  | 434,894,090.92 |   |
| year 5  | 2,802,261,118 | 12.25% | 343,190,497.43 |   |
| year 6  | 3,145,451,616 |  8.16% | 256,813,827.38 |   |
| year 7  | 3,402,265,443 |  5.44% | 185,187,781.58 |   |
| year 8  | 3,587,453,225 |  3.63% | 130,178,458.11 |   |
| year 9  | 3,717,631,683 |  2.42% | 89,934,842.35  |   |
| year 10 | 3,807,566,525 |  1.61% | 61,406,996.78  |   |
| year 11 | 3,868,973,522 |  1.08% |  41,598,230.44 |   |
| year 12 | 3,910,571,752 |  0.72% |  28,030,322.77 |   |
| year 13 | 3,938,602,075 |  0.48% |  18,820,826.28 |   |
| year 14 | 3,957,422,901 |  0.32% |  12,607,175.09 |   |
| year 15 | 3,970,030,076 |  0.21% |  8,431,558.54  |   |
| year 16 | 3,978,461,635 |  0.14% |  5,632,977.00  |   |
| year 17 | 3,984,094,612 |  0.09% |  3,760,635.04  |   |
| year 18 | 3,987,855,247 |  0.06% |  2,509,456.50  |   |
| year 19 | 3,990,364,703 |  0.04% |  1,674,023.76  |   |
| year 20 | 3,992,038,727 |  0.03% |  1,116,484.02  |   |
| year 21 | 3,993,155,211 |  0.02% |  744,530.85    |   |
| year 22 | 3,993,899,742 |  0.01% |  496,446.45    |   |
| year 23 | 3,994,396,189 |  0.01% |  331,005.44    |   |
| year 24 | 3,994,727,194 |  0.01% |  220,688.58    |   |
| year 25 | 3,994,947,883 |  0.00% |  147,133.85    |   |
| year 26 | 3,995,095,016 |  0.00% |  98,092.84     |   |
| year 27 | 3,995,193,109 |  0.00% |  65,396.83     |   |
| year 28 | 3,995,258,506 |  0.00% |  43,598.60     |   |
| year 29 | 3,995,302,105 |  0.00% |  29,066.05     |   |
| year 30 | 3,995,331,171 |  0.00% |  19,377.51     |   |
| year 31 | 3,995,350,548 |  0.00% |  12,918.40     |   |
| year 32 | 3,995,363,467 |  0.00% |  8,612.30      |   |
| year 33 | 3,995,372,079 |  0.00% |  5,741.54      |   |
| year 34 | 3,995,377,820 |  0.00% |  3,827.70      |   |

## Airdrop 

### Airdrop Cycle 1:
| Community              |   # of TERP & THIOL    | Number of Addresses |  |   |
|---------|:----------------:|:------:|:-----------:|---|
| TerpNET Foundation     | 63,000,000 |    1       |    -                |   |
| ATOM Stakers           | 25,683,840 |    164,574 |    -                |   |
| BCNA Stakers           | 8,026,200  |    1,934   |    -                |   |
| TERPNET OG's           | 53,508     |    32      |    -                |   |
| TESTNET SCAVENGER HUNT | 53,508     |    25      |    -                |   |
| GESESIS VALIDATORS     |    10     |    10       |    -                |   |

### Airdrop Cycle 2:
| Community              |  # of TERP & THIOL  | Number of Addresses |  |   |
|---------|:----------------:|:------:|:-----------:|---|
|   Crypto Canna Club    |    -       |    -        |            -        | - |
|   Glaktic Gang         |    -       |    -        |            -        | - |
|   MonsterBuds          |    -       |    -        |            -        | - |
|   Chronic Token        |    -       |    -        |            -        | - |
|   Secret Sesh          |    -       |    -        |            -        | - |
|   ?                    |    -       |    -        |            -        | - |

## Vesting 
As Terp Network continues to progressively decentralize, there are many techniques and methods applied to minimize risk inherited with networks in their infancy. One of these techniques is vesting, which to encourage sustainability & long-term commitment, we will be using vesting plans on all of the genesis TERP tokens airdropped (not including the protocol owned treasury). You can learn more about the [standard Cosmos SDK vesting account](https://docs.cosmos.network/main/modules/auth/vesting).


Tokens that are vesting will only be able to be used for delegating to validators for things like governance and earning rewards. a Cliff Vesting structure will give us time to do things where having tokens in active circulation would not permit viable bootstrapping opportunities.