# Quick Start Guide – ICT/SMC Reversal Strategy Indicator v6

## 30-Second Setup

1. **Copy the code** from `ICT_SMC_Reversal_Strategy.pine`
2. **Open TradingView** → Pine Script Editor
3. **Paste & Save** (name it anything)
4. **Add to Chart** → Select a 4H or Daily chart
5. **Watch the panel** for "3/3 ✅ READY" signals
6. **Done!** Indicator is now live

---

## First 5 Minutes

### Step 1: Apply to Chart
- Use **4H or Daily** timeframe (best performance)
- Apply to Forex, Crypto, or Stocks
- Wait 2-3 bars for initialization

### Step 2: Check the Info Panel
Look for **top-right corner** table showing:
```
Current Bias:    ⚪ NONE
Sweep:           ❌ None
CISD:            ❌ None
IFVG:            ❌ None
Confluence:      0/3
Trade Status:    ⏸️ Idle
```

### Step 3: Watch for Signals
When a **Liquidity Sweep** occurs:
- ✅ Sweep status changes to "BULL" or "BEAR"
- 🟢 Green triangle appears (long) or 🔴 Red triangle (short)
- Entry price, SL, and TP levels populate

---

## Understanding the Setup Sequence

### Phase 1: Liquidity Sweep ✅ (1/3)
**What to look for**:
- Price wicks below a swing low (bullish) or above a swing high (bearish)
- Price closes back in the opposite direction
- A dashed line appears showing the swept level

**On Chart**:
```
Price:  1.2000 (swing low)
        ↓ (wick down)
        1.1950 (extreme low)
        ↑ (closes back up)
        
Status: "✅ BULL" in panel
```

### Phase 2: CISD Confirmation ✅ (2/3)
**What to look for**:
- Strong candle closes above the sweep extreme
- Body is at least 55% of the candle range (configurable)
- Happens within 20 bars of sweep (configurable)

**On Chart**:
```
Bar 1: Sweep detected
Bar 2: Strong bullish candle with large body
       Close > Sweep Extreme
       
Status: "✅ Confirmed" next to CISD in panel
```

### Phase 3: IFVG Detection ✅ (3/3)
**What to look for**:
- A teal/green box appears (bullish) or red box (bearish)
- Box represents an "inverted" fair value gap
- Forms in the recent price action near sweep + CISD

**On Chart**:
```
Old Bearish FVG ━━━━ (was resistance)
       ↓ (price closes above it)
       
IFVG Box ░░░░░░░░░ (now becomes support)
       
Status: "✅ Present" next to IFVG in panel
```

### Signal Fires 🎯 (3/3)
**When all three align**:
- 🟢 Green upward triangle below the bar (long signal)
- 🔴 Red downward triangle above the bar (short signal)
- Entry price filled in
- SL, TP1, TP2, TP3 levels drawn on chart
- Alert fires to your device

**Info Panel Shows**:
```
Entry Price:    1.2120
Stop Level:     1.1950
TP1:            1.2375 (1.5R)
TP2:            1.2545 (2.5R)
TP3:            1.2800 (4.0R)
Current R/R:    —
Trade Status:   🎯 Signal Active
```

---

## Key Settings for Beginners

### Must-Know 5 Settings

#### 1. Swing Detection Length
```
Default: 4 (left) × 4 (right)

Lower (2-3):  More swings detected = More signals (can be noisy)
Higher (5-6): Fewer, higher-quality swings
```
**Recommendation**: Start at 4, leave as-is

#### 2. CISD Body Ratio
```
Default: 0.55 (55%)

Lower (0.45):   Weaker candles accepted (more signals)
Higher (0.70):  Stronger candles required (fewer signals)
```
**Recommendation**: Increase to 0.60 if getting too many false signals

#### 3. Max Bars for Sequence
```
Default: 20

Lower (10):   Tighter timing, stricter confluence
Higher (30):  Looser timing, more signals
```
**Recommendation**: Keep at 20, reduce to 15 if too many signals

#### 4. Require Both CISD & IFVG
```
Default: ON (TRUE)

ON:   Signal fires only when all 3 elements confirmed (safest)
OFF:  Signal fires with just CISD + Sweep (more aggressive)
```
**Recommendation**: Keep ON for beginners

#### 5. Enable HTF Bias
```
Default: OFF

OFF:   Trades any direction (more signals)
ON:    Trades only with Daily trend (fewer, higher-quality signals)
```
**Recommendation**: Enable on lower timeframes (5m, 15m, 1H)

---

## Visual Guide – What to Look For

### ✅ Perfect Bullish Setup

```
                    ENTRY → 🟢
                    TP3 ----
                    TP2 ----
                    TP1 ----
            ╔════════════════════════╗
            ║   IFVG Box (Support)   ║  ← Teal shaded zone
            ╚════════════════════════╝
   CISD     ↗ (Strong close > extreme)
   ━━━━━━━━━
     ↑
   SWEEP ─ (Dashed line at wick low)
   ━━━━━━
     ↓
  EXTREME LOW ← Price wicked here
```

### ✅ Perfect Bearish Setup

```
  EXTREME HIGH ← Price wicked here
   ━━━━━━
     ↑
   SWEEP ─ (Dashed line at wick high)
   ━━━━━━
   CISD     ↙ (Strong close < extreme)
   ━━━━━━━━━
            ╔════════════════════════╗
            ║   IFVG Box (Resist.)   ║  ← Red shaded zone
            ╚════════════════════════╝
                    TP1 ----
                    TP2 ----
                    TP3 ----
                    ENTRY → 🔴
```

---

## Real Trade Example

### EURUSD 4H – Long Signal

```
Monday 10:00 UTC
┌─────────────────────────────────────────┐
│ Swing Low Identified: 1.0850            │
└─────────────────────────────────────────┘

Monday 14:00 UTC (Bar 1)
┌─────────────────────────────────────────┐
│ Price wicks to 1.0820 (below swing)     │
│ Closes at 1.0865 (back above)           │
│ Status: ✅ SWEEP (BULL) – 1/3          │
└─────────────────────────────────────────┘

Monday 18:00 UTC (Bar 2)
┌─────────────────────────────────────────┐
│ Strong bullish candle                   │
│ Body: 80% of range (> 55% required)     │
│ Close: 1.0920 (> 1.0865 extreme)        │
│ Status: ✅ CISD Confirmed – 2/3        │
└─────────────────────────────────────────┘

Tuesday 06:00 UTC (Bar 4)
┌─────────────────────────────────────────┐
│ Price closes above old bearish FVG      │
│ IFVG zone forms (1.0900–1.0910)         │
│ Status: ✅ IFVG Present – 3/3          │
│                                          │
│ 🎯 SIGNAL FIRES!                        │
│ Entry: 1.0920                           │
│ SL: 1.0820                              │
│ Risk: 100 pips                          │
│ TP1: 1.0970 (1.5R = 150 pips)          │
│ TP2: 1.1020 (2.5R = 250 pips)          │
│ TP3: 1.1070 (4.0R = 400 pips)          │
└─────────────────────────────────────────┘

Result: Price rises to 1.1050 ✅ Hit TP2 + Partial TP3
Profit: 2.5R on 50% of position + 3R on 50% = 2.75R average
```

---

## Common Beginner Mistakes

### ❌ Mistake 1: Expecting Signals Every Day
**Why it happens**: Every setup is different; confluences require specific conditions

**Fix**: Run on multiple timeframes simultaneously (5m, 1H, 4H, Daily)

### ❌ Mistake 2: Ignoring the Info Panel
**Why it happens**: Too focused on chart, missing status updates

**Fix**: Glance at panel every 2-3 bars to track confluence progress

### ❌ Mistake 3: Not Adjusting Settings for Timeframe
**Why it happens**: One-size-fits-all mindset

**Fix**: Use template settings:
- **5m Chart**: Swing bars = 2, CISD ratio = 0.50, HTF = 15m
- **1H Chart**: Swing bars = 3, CISD ratio = 0.55, HTF = 4H
- **4H Chart**: Swing bars = 4, CISD ratio = 0.60, HTF = Daily
- **Daily**: Swing bars = 5, CISD ratio = 0.65, HTF = Weekly

### ❌ Mistake 4: Trading Without Stop Loss
**Why it happens**: Indicators can fail; market is unpredictable

**Fix**: ALWAYS use the SL level provided. Never remove it.

### ❌ Mistake 5: Chasing Entries After Signal
**Why it happens**: FOMO (fear of missing out)

**Fix**: Only enter when signal appears. Past signals don't repeat.

---

## Tip: Demo Account First!

### Recommended Progression

```
Week 1: Paper Trade Only
  └─ Apply to 4H chart
  └─ Track signals but don't execute
  └─ Verify accuracy for 30+ signals

Week 2: Small Real Trades (1-2 signals)
  └─ Trade only the clearest setups
  └─ Use minimum position size
  └─ Document results

Week 3: Live Scaling
  └─ Increase position size gradually
  └─ Adjust settings based on performance
  └─ Refine filters and HTF timeframe

Month 2+: Full Implementation
  └─ Automate alerts
  └─ Run on multiple symbols
  └─ Optimize for your trading style
```

---

## Alerts & Notifications

### Enable Alerts (TradingView)

1. **Open Indicator Settings**
2. **Look for "Alert" section** (check mark icon)
3. **Enable**: "Long Signal" and "Short Signal"
4. **Click "Create Alert"** on the indicator
5. **Set Frequency**: "Once Per Bar Close"
6. **Add Notification**: Email, SMS, or Push

### Alert Messages

```
🟢 LONG SIGNAL FIRED - Entry: 1.2120 | SL: 1.1950

🔴 SHORT SIGNAL FIRED - Entry: 0.9650 | SL: 0.9850
```

---

## Troubleshooting Checklist

| Issue | Cause | Fix |
|-------|-------|-----|
| No signals for days | Settings too strict | Lower body ratio to 0.50 |
| Too many false signals | Settings too loose | Raise body ratio to 0.65 |
| Sweep line not visible | Fade time too short | Increase "Fade After Bars" to 50 |
| Info panel overlaps chart | Wrong position | Change "Panel Position" in settings |
| HTF bias shows "NONE" | Symbol format wrong | Use correct format (EURUSD not EUR/USD) |
| Chart lags/freezes | Too many objects | Reduce IFVG lookback to 50 |

---

## Next Steps

### Learn More
1. Read **README.md** for detailed strategy explanation
2. Read **UPGRADE_GUIDE_v6.md** for technical details
3. Watch YouTube tutorials (search "ICT/SMC reversal indicator")

### Join Community
- GitHub: https://github.com/EMK-C29/ict-smc-reversal-indicator
- TradingView: Search indicator name in community
- Discord: Join Pine Script community servers

### Customize
1. Change colors to match your theme
2. Adjust RR multiples (TP targets) for your strategy
3. Enable/disable filters (HTF, Sessions)

---

## Summary

✅ **You now know**:
- How to install the indicator
- What Liquidity Sweep, CISD, and IFVG mean
- How to read the info panel
- 5 key settings to adjust
- How to spot perfect setups
- How to avoid common mistakes

✅ **You're ready to**:
- Apply to your charts
- Paper trade for 1-2 weeks
- Go live with small positions
- Optimize for your trading style

---

## Remember

> **"The indicator is a guide, not a crystal ball."**
> 
> Backtest thoroughly, paper trade first, and manage risk properly.
> No indicator is 100% accurate. Always use stop losses.

---

**Good luck! 🚀 Happy trading!**

**Questions?** Check the README.md or open an issue on GitHub.

---

**Version**: 6.0  
**Last Updated**: September 15, 2026  
**Status**: Production Ready ✅