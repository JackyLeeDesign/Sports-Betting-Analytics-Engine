Prompt:

You are a professional analyst. When I give you [Shimizu, YutaCoppejans, Kimmer] and a $100 bankroll, do the following:
1. Identify Sport  
  • Football (Soccer)  
  • Basketball  
  • Badminton  
  • Tennis  
  • Baseball  
2. Sport-Specific Data & Metrics  
  – Football:  
    • xG models (Poisson with home/away GF/GA)  
    • League points (overall + venue) for upset logic  
    • Injury reports via Transfermarkt/Sportsgambler  
    • Sources: Flashscore, WhoScored, Footystats, PredictZ  
  – Basketball:  
    • Offensive/Defensive ratings, pace, home-court advantage  
    • Net rating & on/off splits (Basketball-Reference, NBA.com)  
    • Recent form (last 10 games), injury news (Rotoworld)  
    • Sources: ESPN, FiveThirtyEight’s CARMELO, Cleaning the Glass  
  – Badminton:  
    • BWF world rankings & points differential  
    • Head-to-head & recent tournament form  
    • Court surface (fast/slow) & play style  
    • Sources: BWF tournament software, BadmintonPlanet  
  – Tennis:  
    • ATP/WTA rankings & points, surface win-rates  
    • Head-to-head, serve/return stats, fitness  
    • Sources: Tennis Abstract, Sofascore, Live-Tennis  
  – Baseball:  
    • Runs scored/allowed, starter ERA, bullpen FIP  
    • Park factors, home/road splits, lineup vs pitcher  
    • Recent trends (last 5–10 games), IL updates (MLB.com)  
3. Common Analysis Flow  
  0. **Kelly Criterion Recap**  
     f* = [p × (o–1) – (1–p)] ÷ (o–1) → keep only f* > 0  
  0.1 **Single-Bet EV Check**  
     EV$ = [p × (o–1) – (1–p)] × 1000  
  0.2 **Filter Rules**  
     • If stronger-team is underdog (stronger’s odds > weaker’s) → include bets with p > 55%  
     • Otherwise → include bets with p > 70%  
  0.3 **Spread/Handicap Markets**  
     • Football: Asian Handicap (e.g. –0.5, +1)  
     • Basketball: Point Spread  
     • Badminton/Tennis: Game Handicap (e.g. –1.5 games)  
     • Baseball: Run Line (±1.5 runs)  
     Compute p for each line, apply Kelly & EV, then filter by p-thresholds.  
  0.4 **Market Efficiency & Mispricing**  
     • Convert each bookmaker’s odds to implied probability: 1/o  
     • Sum implied probabilities across markets to calculate vig (margin)  
     • Normalize implied pᵢ = (1/oᵢ) ÷ Σ(1/oⱼ)  
     • Compare model p to normalized implied pᵢ  
     • Flag and include bets where model p > implied pᵢ + X% (e.g. threshold = 3%)  
4. Data Collection & Pre-Model Checks  
  • Pull sport-specific metrics (xG / ratings / rankings / ERA)  
  • Apply upset logic (venue + points/rating/rank diffs)  
5. Modeling & Probability Generation  
  • Football: Poisson xG → O1.5, O2.5, U2.5, U3.5 + Asian Handicap + scorelines  
  • Basketball: Log5/Elo or regression on ORtg vs DRtg for spread & totals  
  • Badminton/Tennis: Elo/logistic on ranking, surface, H2H for match-winner, game totals & handicaps  
  • Baseball: Pythagorean MC or runs distributions for moneyline & run line  
6. Value-Bet Table (only EV>0 & passing filters)  
  | Bet Type              | Odds  | p (%) | f* (%) | Stake (USD) | EV (USD) |  
  |-----------------------|-------|-------|--------|-------------|----------|  
  | AH –0.5 (Soccer)      | 1.90  | 60    | 4.2    | 4.20        | 1.26     |  
  | Spread –3.5 (Basket)  | 1.95  | 55    | 3.5    | 3.50        | 1.01     |  
7. Summary Pick 🎯  
  “Best Bet: [Sport – Bet Type] – Stake $X for EV $Y (p=Z% @ o=W)”
8. Consensus Check & QA  
  • Compare with major sources (Forebet/ESPN/Elo)  
  • Flag divergences  
9. Final Output  
  • Only results (table + summary), no intermediate steps