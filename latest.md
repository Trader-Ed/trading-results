# Exit-variant comparison, 2026-06-01 to 2026-10-23, $2,500 equity (run 2026-10-26)

### atr

| Variant | Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|
| baseline | 84 | 36.9% | $37.24 | $-29.73 | $-421.47 | $-5.02 | +13.8% ($+345) | -8.1% ($-202) |
| v0_no_slippage | 84 | 44.0% | $40.13 | $-25.04 | $+308.00 | $+3.67 | +14.3% ($+358) | -6.6% ($-165) |
| v1_volume_fade_3 | 83 | 32.5% | $53.71 | $-31.88 | $-335.39 | $-4.04 | +13.8% ($+345) | -8.1% ($-202) |
| v2_no_volume_fade | 83 | 31.3% | $61.18 | $-33.86 | $-339.36 | $-4.09 | +13.8% ($+345) | -8.1% ($-202) |
| v3_wider_stops | 83 | 37.3% | $60.12 | $-34.38 | $+75.70 | $+0.91 | +13.8% ($+345) | -7.4% ($-185) |
| v4_no_bar_exits | 82 | 31.7% | $64.28 | $-35.37 | $-309.53 | $-3.77 | +13.8% ($+345) | -9.4% ($-235) |

### spy

| Variant | Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|
| baseline | 64 | 25.0% | $31.85 | $-17.62 | $-336.09 | $-5.25 | +4.1% ($+102) | -3.1% ($-78) |
| v0_no_slippage | 64 | 32.8% | $28.70 | $-14.27 | $-10.80 | $-0.17 | +4.3% ($+108) | -2.4% ($-60) |
| v1_volume_fade_3 | 62 | 30.6% | $31.78 | $-21.37 | $-314.92 | $-5.08 | +4.1% ($+102) | -2.6% ($-65) |
| v2_no_volume_fade | 62 | 30.6% | $32.33 | $-22.30 | $-344.64 | $-5.56 | +4.1% ($+102) | -3.1% ($-78) |
| v3_wider_stops | 64 | 23.4% | $42.67 | $-21.87 | $-431.59 | $-6.74 | +5.5% ($+138) | -3.3% ($-82) |
| v4_no_bar_exits | 62 | 35.5% | $32.13 | $-24.86 | $-287.54 | $-4.64 | +4.1% ($+102) | -3.1% ($-78) |

## atr/baseline

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 84 | 36.9% | $+37.24 | $-29.73 | $-421.47 | $-5.02 | $+346.00 | $-96.24 | $+346.00 | $-201.91 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 28 | 32.1% | $+92.19 | $+3.29 |
| NVDA | 1 | 0.0% | $-36.35 | $-36.35 |
| TSLA | 36 | 38.9% | $-57.99 | $-1.61 |
| META | 19 | 42.1% | $-419.32 | $-22.07 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| profit_target | 1 | 100.0% | $+146.22 | $+146.22 |
| volume_faded | 32 | 50.0% | $+2.22 | $+0.07 |
| setup_failed | 4 | 0.0% | $-136.44 | $-34.11 |
| hard_stop | 6 | 0.0% | $-378.62 | $-63.10 |
| trailing_stop | 40 | 32.5% | $-400.85 | $-10.02 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 45 | 31.1% | $-34.26 | $-0.76 |
| short | 39 | 43.6% | $-387.21 | $-9.93 |

## atr/v0_no_slippage

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 84 | 44.0% | $+40.13 | $-25.04 | $+308.00 | $+3.67 | $+358.00 | $-82.00 | $+358.00 | $-166.10 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 28 | 42.9% | $+287.00 | $+10.25 |
| TSLA | 36 | 44.4% | $+239.50 | $+6.65 |
| NVDA | 1 | 0.0% | $-33.00 | $-33.00 |
| META | 19 | 47.4% | $-185.50 | $-9.76 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+358.00 | $+358.00 |
| volume_faded | 32 | 59.4% | $+304.00 | $+9.50 |
| profit_target | 1 | 100.0% | $+152.50 | $+152.50 |
| setup_failed | 3 | 0.0% | $-61.00 | $-20.33 |
| trailing_stop | 43 | 37.2% | $-206.30 | $-4.80 |
| hard_stop | 4 | 0.0% | $-239.20 | $-59.80 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 45 | 37.8% | $+334.20 | $+7.43 |
| short | 39 | 51.3% | $-26.20 | $-0.67 |

## atr/v1_volume_fade_3

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 83 | 32.5% | $+53.71 | $-31.88 | $-335.39 | $-4.04 | $+346.00 | $-96.24 | $+346.00 | $-201.91 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 35 | 40.0% | $+155.39 | $+4.44 |
| NVDA | 1 | 0.0% | $-36.35 | $-36.35 |
| QQQ | 28 | 17.9% | $-103.33 | $-3.69 |
| META | 19 | 42.1% | $-351.10 | $-18.48 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 4 | 100.0% | $+535.50 | $+133.88 |
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| time_stop | 1 | 100.0% | $+69.24 | $+69.24 |
| volume_faded | 9 | 44.4% | $-29.50 | $-3.28 |
| setup_failed | 7 | 0.0% | $-229.98 | $-32.85 |
| hard_stop | 7 | 0.0% | $-435.02 | $-62.15 |
| trailing_stop | 54 | 31.5% | $-591.63 | $-10.96 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 44 | 27.3% | $-106.79 | $-2.43 |
| short | 39 | 38.5% | $-228.60 | $-5.86 |

## atr/v2_no_volume_fade

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 83 | 31.3% | $+61.18 | $-33.86 | $-339.36 | $-4.09 | $+346.00 | $-96.24 | $+346.00 | $-201.91 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 35 | 40.0% | $+276.62 | $+7.90 |
| NVDA | 1 | 0.0% | $-36.35 | $-36.35 |
| QQQ | 28 | 14.3% | $-197.51 | $-7.05 |
| META | 19 | 42.1% | $-382.12 | $-20.11 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 5 | 100.0% | $+679.32 | $+135.86 |
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| time_stop | 3 | 100.0% | $+124.22 | $+41.41 |
| setup_failed | 8 | 0.0% | $-260.34 | $-32.54 |
| hard_stop | 7 | 0.0% | $-435.02 | $-62.15 |
| trailing_stop | 59 | 28.8% | $-793.54 | $-13.45 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 44 | 27.3% | $+6.81 | $+0.15 |
| short | 39 | 35.9% | $-346.17 | $-8.88 |

## atr/v3_wider_stops

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 83 | 37.3% | $+60.12 | $-34.38 | $+75.70 | $+0.91 | $+346.00 | $-95.20 | $+346.00 | $-184.00 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 27 | 40.7% | $+352.30 | $+13.05 |
| NVDA | 1 | 0.0% | $-39.92 | $-39.92 |
| META | 19 | 36.8% | $-79.74 | $-4.20 |
| TSLA | 36 | 36.1% | $-156.94 | $-4.36 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 6 | 83.3% | $+734.40 | $+122.40 |
| profit_target | 1 | 100.0% | $+146.22 | $+146.22 |
| volume_faded | 35 | 45.7% | $-142.72 | $-4.08 |
| setup_failed | 7 | 0.0% | $-303.16 | $-43.31 |
| trailing_stop | 34 | 26.5% | $-359.04 | $-10.56 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 44 | 38.6% | $+328.38 | $+7.46 |
| short | 39 | 35.9% | $-252.68 | $-6.48 |

## atr/v4_no_bar_exits

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 82 | 31.7% | $+64.28 | $-35.37 | $-309.53 | $-3.77 | $+346.00 | $-96.24 | $+346.00 | $-234.60 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 35 | 40.0% | $+273.97 | $+7.83 |
| NVDA | 1 | 0.0% | $-36.35 | $-36.35 |
| QQQ | 28 | 14.3% | $-251.15 | $-8.97 |
| META | 18 | 44.4% | $-296.00 | $-16.44 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 5 | 100.0% | $+679.32 | $+135.86 |
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| time_stop | 4 | 100.0% | $+214.36 | $+53.59 |
| hard_stop | 9 | 0.0% | $-503.54 | $-55.95 |
| trailing_stop | 63 | 25.4% | $-1,045.67 | $-16.60 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 43 | 27.9% | $+62.30 | $+1.45 |
| short | 39 | 35.9% | $-371.83 | $-9.53 |

## spy/baseline

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 64 | 25.0% | $+31.85 | $-17.62 | $-336.09 | $-5.25 | $+102.59 | $-48.03 | $+102.59 | $-76.62 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 64 | 25.0% | $-336.09 | $-5.25 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 2 | 100.0% | $+204.22 | $+102.11 |
| hard_stop | 2 | 0.0% | $-65.88 | $-32.94 |
| volume_faded | 25 | 20.0% | $-148.00 | $-5.92 |
| trailing_stop | 27 | 33.3% | $-160.47 | $-5.94 |
| setup_failed | 8 | 0.0% | $-165.96 | $-20.75 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 32 | 21.9% | $-136.12 | $-4.25 |
| long | 32 | 28.1% | $-199.97 | $-6.25 |

## spy/v0_no_slippage

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 64 | 32.8% | $+28.70 | $-14.27 | $-10.80 | $-0.17 | $+107.00 | $-43.60 | $+107.00 | $-61.00 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 64 | 32.8% | $-10.80 | $-0.17 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 2 | 100.0% | $+213.00 | $+106.50 |
| volume_faded | 25 | 36.0% | $-2.00 | $-0.08 |
| hard_stop | 1 | 0.0% | $-36.60 | $-36.60 |
| trailing_stop | 27 | 37.0% | $-38.20 | $-1.41 |
| setup_failed | 9 | 0.0% | $-147.00 | $-16.33 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 32 | 31.2% | $+40.80 | $+1.27 |
| long | 32 | 34.4% | $-51.60 | $-1.61 |

## spy/v1_volume_fade_3

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 62 | 30.6% | $+31.78 | $-21.37 | $-314.92 | $-5.08 | $+102.59 | $-48.03 | $+102.59 | $-63.88 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 62 | 30.6% | $-314.92 | $-5.08 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 3 | 100.0% | $+293.87 | $+97.96 |
| volume_faded | 13 | 38.5% | $-46.50 | $-3.58 |
| hard_stop | 3 | 0.0% | $-96.95 | $-32.32 |
| setup_failed | 9 | 0.0% | $-207.20 | $-23.02 |
| trailing_stop | 34 | 32.4% | $-258.14 | $-7.59 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 31 | 32.3% | $-119.66 | $-3.86 |
| short | 31 | 29.0% | $-195.26 | $-6.30 |

## spy/v2_no_volume_fade

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 62 | 30.6% | $+32.33 | $-22.30 | $-344.64 | $-5.56 | $+102.59 | $-48.03 | $+102.59 | $-77.33 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 62 | 30.6% | $-344.64 | $-5.56 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 3 | 100.0% | $+293.87 | $+97.96 |
| time_stop | 7 | 71.4% | $+62.18 | $+8.88 |
| hard_stop | 3 | 0.0% | $-96.95 | $-32.32 |
| setup_failed | 11 | 0.0% | $-259.86 | $-23.62 |
| trailing_stop | 38 | 28.9% | $-343.88 | $-9.05 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 31 | 32.3% | $-158.20 | $-5.10 |
| short | 31 | 29.0% | $-186.44 | $-6.01 |

## spy/v3_wider_stops

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 64 | 23.4% | $+42.67 | $-21.87 | $-431.59 | $-6.74 | $+136.76 | $-63.60 | $+136.76 | $-81.68 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 64 | 23.4% | $-431.59 | $-6.74 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 2 | 100.0% | $+204.22 | $+102.11 |
| noon_shutdown | 3 | 100.0% | $+199.82 | $+66.61 |
| hard_stop | 1 | 0.0% | $-37.15 | $-37.15 |
| volume_faded | 26 | 23.1% | $-113.84 | $-4.38 |
| setup_failed | 11 | 0.0% | $-307.02 | $-27.91 |
| trailing_stop | 21 | 19.0% | $-377.62 | $-17.98 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 32 | 28.1% | $-142.50 | $-4.45 |
| short | 32 | 18.8% | $-289.09 | $-9.03 |

## spy/v4_no_bar_exits

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 62 | 35.5% | $+32.13 | $-24.86 | $-287.54 | $-4.64 | $+102.59 | $-48.03 | $+102.59 | $-77.33 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 62 | 35.5% | $-287.54 | $-4.64 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 3 | 100.0% | $+293.87 | $+97.96 |
| time_stop | 9 | 77.8% | $+148.66 | $+16.52 |
| hard_stop | 4 | 0.0% | $-127.13 | $-31.78 |
| trailing_stop | 46 | 26.1% | $-602.94 | $-13.11 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 31 | 38.7% | $-108.77 | $-3.51 |
| short | 31 | 32.3% | $-178.77 | $-5.77 |

---

Full per-trade tables: [history/2026-10-27-exit-variants.md](history/2026-10-27-exit-variants.md)
