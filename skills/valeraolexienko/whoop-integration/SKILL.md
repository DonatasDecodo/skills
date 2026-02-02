---
name: whoop-integration
description: Integrate with WHOOP fitness tracker API to monitor sleep, recovery, and strain data. Use when you need to check sleep quality, recovery scores, analyze fitness patterns, set up morning behavior adjustments based on sleep performance, or create automated health monitoring workflows. Supports OAuth authentication, sleep performance tracking, and adaptive assistant behavior.
metadata:
  {
    "openclaw":
      {
        "emoji": "🏃‍♀️",
        "requires": { "env": ["WHOOP_CLIENT_ID", "WHOOP_CLIENT_SECRET"] },
        "primaryEnv": "WHOOP_CLIENT_SECRET",
      }
  }
---

# WHOOP Integration

Monitor sleep, recovery, and strain data from WHOOP fitness tracker. Adjust assistant behavior based on sleep quality.

## Setup

1. **Configure credentials** (add to OpenClaw config env section):

Edit `~/.openclaw/openclaw.json` and add to the `env` section:
```json
{
  "env": {
    "WHOOP_CLIENT_ID": "your_client_id_here",
    "WHOOP_CLIENT_SECRET": "your_client_secret_here"
  }
}
```

**Alternative methods:**
- Environment variables: `WHOOP_CLIENT_ID`, `WHOOP_CLIENT_SECRET`  
- OpenClaw skills config: `openclaw configure --section skills` (fallback only)

2. **Run OAuth authentication**:
```bash
python3 scripts/oauth_setup.py
```

## Features

### Sleep Monitoring
- Sleep performance percentage (0-100%)
- Sleep efficiency and duration
- REM, deep sleep, light sleep stages
- Disturbances and sleep consistency

### Recovery Tracking
- Recovery score (0-100)
- HRV (Heart Rate Variability)
- Resting heart rate
- Skin temperature

### Adaptive Behavior
Assistant automatically adjusts communication style based on sleep quality:

**Poor sleep (<70% performance):**
- Shorter, more direct responses
- Softer tone and encouragement
- Reduced complex task suggestions
- More empathy and understanding

**Great sleep (>90% performance):**
- Energetic and enthusiastic tone
- Suggest more ambitious tasks
- Proactive project ideas
- Higher energy communication

## API Usage

### Get Latest Sleep Data
```python
from scripts.whoop_client import WhoopClient

client = WhoopClient()
sleep_data = client.get_latest_sleep()
print(f"Sleep performance: {sleep_data['score']['sleep_performance_percentage']}%")
```

### Morning Check (Automated)
Set up morning cron job to automatically check sleep and adjust behavior:
```bash
# Add to cron (runs at 8:00 AM daily)
0 8 * * * python3 /home/valera/.openclaw/workspace/whoop-integration/scripts/morning_check.py
```

## Configuration

Required environment variables:
- `WHOOP_CLIENT_ID` - OAuth client ID
- `WHOOP_CLIENT_SECRET` - OAuth client secret  
- `WHOOP_ACCESS_TOKEN` - User access token (obtained via OAuth)
- `WHOOP_REFRESH_TOKEN` - Refresh token for token renewal

## References

See [API_REFERENCE.md](references/API_REFERENCE.md) for complete WHOOP API documentation and [OAUTH_FLOW.md](references/OAUTH_FLOW.md) for OAuth setup details.