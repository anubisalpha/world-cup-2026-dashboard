# Tournament Dashboard Creation Guide

## Overview

This guide explains how to create a tournament tracking dashboard similar to the World Cup 2026 dashboard. It's a single-file HTML application with JavaScript and CSS that tracks group stage results, calculates standings, and manages knockout brackets.

**Features:**
- Live group stage match schedule
- Editable match scores with automatic point calculation
- Dynamic group standings with tiebreaker tracking
- Knockout bracket that populates from group results
- Third-place playoff tracking
- Export/Import results as JSON
- Responsive design (desktop, tablet, mobile)
- All data persists in browser localStorage

---

## Quick Start

1. Copy the `world-cup-2026.html` file as your template
2. Replace tournament name and dates
3. Update all data arrays with your tournament information
4. Customize colors and branding
5. Test thoroughly before sharing

---

## File Structure

The entire application is one self-contained HTML file with:
- **CSS**: Styling and responsive layouts (lines ~8-550)
- **HTML**: DOM structure (lines ~555-685)
- **JavaScript**: All logic and rendering (lines ~688-end)
- **Data Objects**: Tournament information (teams, matches, venues, etc.)

---

## Step-by-Step Customization

### 1. Update Tournament Metadata

Change these values at the top of the HTML:

```html
<title>Your Tournament Name</title>
<h1>Your Tournament Name</h1>
<p>Live Match Schedule & Results</p>
<p style="font-size: 0.75em; color: #999; margin-top: 2px;">created by Your Name and Claude.</p>
<p style="font-size: 0.7em; color: #bbb; margin-top: 0;"><a href="mailto:your.email@example.com">your.email@example.com</a></p>
```

### 2. Update the Logo

In the `<header>` section, change the logo URL:

```html
<img src="https://your-logo-url.com/logo.png" alt="Tournament Logo">
```

### 3. Define Your Tournament Structure

**For groups:** Modify the `groups` object in the JavaScript section:

```javascript
const groups = {
    'A': [
        { name: 'Team 1', pts: 0, gf: 0, ga: 0 },
        { name: 'Team 2', pts: 0, gf: 0, ga: 0 },
        { name: 'Team 3', pts: 0, gf: 0, ga: 0 },
        { name: 'Team 4', pts: 0, gf: 0, ga: 0 }
    ],
    'B': [ /* ... */ ],
    // etc for all groups
};
```

**Key points:**
- Each group must have 4 teams
- `pts`: points (auto-calculated, start at 0)
- `gf`: goals for (auto-calculated)
- `ga`: goals against (auto-calculated)

### 4. Add All Matches

Update the `matches` array with complete schedule:

```javascript
const matches = [
    { 
        date: '2024-06-10', 
        time: '20:00', 
        stage: 'Group A', 
        team1: 'Team Name', 
        team2: 'Other Team',
        venue: 'Stadium Name', 
        location: 'City, Country', 
        channels: ['Channel 1', 'Channel 2'] 
    },
    // repeat for all matches
];
```

**Required fields:**
- `date`: YYYY-MM-DD format
- `time`: HH:MM format (24-hour)
- `stage`: "Group X" or tournament stage name
- `team1`, `team2`: exact team names
- `venue`: stadium name
- `location`: city/country
- `channels`: broadcast channels

### 5. Add Team Flags

The dashboard uses emoji flags. Update the `teamFlags` object:

```javascript
const teamFlags = {
    'Team Name': '🇦🇺',  // flag emoji
    'Other Team': '🇫🇷',
    // etc
};
```

You can also use image URLs:
```javascript
'Team Name': 'https://example.com/team-flag.png',
```

### 6. Configure Broadcast Channels

Update `channelUrls` with your broadcast partners:

```javascript
const channelUrls = {
    'Channel 1': 'https://channel1.com/sport',
    'Channel 2': 'https://channel2.com/',
    'Streaming': 'https://streaming.example.com/',
};
```

### 7. Add Stadium Details

Update `stadiumDetails` with venue information:

```javascript
const stadiumDetails = {
    'Stadium Name': { 
        capacity: '50,000', 
        city: 'City Name, Country', 
        stadium: 'Full Stadium Name' 
    },
    // repeat for all venues
};
```

### 8. Link Stadium Pages

Update `stadiumUrls` to link to venue information:

```javascript
const stadiumUrls = {
    'Stadium Name': 'https://wikipedia.org/wiki/Stadium',
    // etc
};
```

### 9. Link Team Information Pages

Update `fifaTeamUrls` to link to team profiles:

```javascript
const fifaTeamUrls = {
    'Team Name': 'https://example.com/teams/team-name',
    // all 32 teams
};
```

### 10. Define Group Matches

The `groupMatches` array maps each match for result tracking:

```javascript
const groupMatches = [
    { id: 'GM1', date: '2024-06-10', group: 'A', team1: 'Team A', team2: 'Team B' },
    { id: 'GM2', date: '2024-06-10', group: 'A', team1: 'Team C', team2: 'Team D' },
    // ID format: GM1, GM2, GM3... for group matches
    // Must match the matches array
];
```

### 11. Configure Knockout Matches

Update `knockoutStages` for your bracket structure:

```javascript
const knockoutStages = [
    { 
        id: 'KO1', 
        date: '2024-07-01', 
        stage: 'Round of 16', 
        team1: 'Group A 1st', 
        team2: 'Group B 2nd', 
        stadium: 'Stadium Name', 
        channels: ['Channel 1', 'Channel 2'] 
    },
    // ID format: KO1, KO2... for knockout matches
    // ID format: R16-1, R16-2... for round of 16
    // ID format: QF-1, QF-2... for quarterfinals
    // ID format: SF-1, SF-2... for semifinals
    // ID format: FINAL for the final
];
```

**Team reference formats:**
- `'Group A 1st'` - Winner of Group A
- `'Group A 2nd'` - Runner-up of Group A
- `'KO1 Winner'` - Winner of knockout match KO1
- `'3rd Place Group A/B'` - Third place from groups A or B

### 12. Customize Dates

Update the tournament dates:

```javascript
const today = '2024-06-10';  // current/start date
const knockoutStartDate = '2024-06-29';  // when knockout stage begins
```

### 13. Update Third-Place Playoff

Modify the `thirdPlaceMatch` object:

```javascript
const thirdPlaceMatch = {
    id: '3P',
    date: '2024-07-17',
    stage: 'Third Place Match',
    team1: '3rd Place Group A/B/C/D',
    team2: '3rd Place Group E/F/G/H',
    stadium: 'Stadium Name',
    channels: ['Channel 1']
};
```

### 14. Customize Colors (Optional)

Update the color scheme in the CSS `<style>` section:

```css
/* Main theme color */
color: #1e3c72;  /* Change to your color */

/* Background gradient */
background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
```

Common colors to customize:
- `#1e3c72` - Primary blue
- `#2a5298` - Secondary blue
- `#1e3c72` - Sidebar title background
- Text colors, borders, etc.

### 15. Update Features List

Change the features displayed in the header:

```html
<div>✓ Live group standings</div>
<div>✓ Dynamic knockout bracket</div>
<!-- etc -->
```

---

## Data Validation Checklist

Before testing, verify:

- ✓ All team names are spelled consistently across files
- ✓ All dates are in YYYY-MM-DD format
- ✓ All times are in HH:MM format (24-hour)
- ✓ Group structure: exactly 4 teams per group
- ✓ Total matches: (4 teams × 3 games per team) ÷ 2 = 48 matches per 12 groups
- ✓ Knockout team references match group structure
- ✓ All stadiums in matches array are defined in stadiumDetails
- ✓ All channels are defined in channelUrls
- ✓ All teams have flag emojis/URLs defined
- ✓ No duplicate match IDs (GM1-GMX, KO1-KOX, R16-1-R16-X, etc.)

---

## Testing

### 1. Basic Functionality
- [ ] Open the HTML file in a browser
- [ ] Group Stages tab shows match schedule
- [ ] Can select different dates
- [ ] Group selector buttons work (A-L + Knockout)
- [ ] Group standings display correctly

### 2. Results Entry
- [ ] Click "Group Stage Results" tab
- [ ] Can enter match scores
- [ ] Points calculate correctly (3 for win, 1 for draw, 0 for loss)
- [ ] Group standings update automatically
- [ ] Goal difference and goals for display correctly

### 3. Tiebreaker Resolution
- [ ] When two teams have same points, second tiebreaker (goal difference) appears
- [ ] Can click tied teams to manually select which advances
- [ ] Can only select after all 3 matches are entered for that group

### 4. Knockout Bracket
- [ ] Click "Knockout Stage" tab
- [ ] Shows third-place playoff section
- [ ] Knockout matches show "TBD" for teams not yet qualified
- [ ] As group results are entered, teams populate in bracket
- [ ] Can enter knockout match scores
- [ ] Later rounds populate with winners from previous rounds

### 5. Data Persistence
- [ ] Enter some results
- [ ] Refresh the page
- [ ] Results are still there (localStorage working)
- [ ] Can export results as JSON
- [ ] Can import previously exported JSON

### 6. Responsive Design
- [ ] Test on desktop (full layout)
- [ ] Test on tablet (sidebar stacks above content)
- [ ] Test on mobile (all content single column)

---

## Advanced Customization

### Change Point System

Modify the `calculatePoints()` function:

```javascript
function calculatePoints(score1, score2) {
    if (score1 > score2) return { team1: 3, team2: 0 };  // Change these values
    if (score1 < score2) return { team1: 0, team2: 3 };
    return { team1: 1, team2: 1 };
}
```

### Modify Group Count

If your tournament has different number of groups:
1. Adjust the `groups` object
2. Update group buttons HTML (add/remove A-L buttons)
3. Create corresponding knockout structure
4. Update third-place playoff references

### Change Number of Teams Per Group

If groups don't have 4 teams:
1. Update `groups` object
2. Update match count in validation
3. May need to adjust knockout structure

---

## Deployment

### Local Sharing
1. Send the HTML file via email
2. Recipients open file directly in browser
3. No server required

### Web Hosting
1. Upload HTML to web hosting service
2. Share the URL
3. Each user will have their own localStorage results
4. Results don't sync across users (local only)

### Making Results Shareable Across Users

To sync results across multiple devices:
1. Extend the code to save results to a database
2. Add a sync function that uploads/downloads results
3. Requires backend server setup

---

## File Size Optimization

### Original file: ~100 KB

### Options for sending via email:

1. **Minified HTML** (~78 KB)
   ```bash
   cat tournament.html | tr -s ' ' | tr '\n' ' ' | sed 's/> </></g' > tournament.min.html
   ```

2. **Gzip Compressed** (~16 KB) - Recommended
   ```bash
   gzip -c tournament.html > tournament.html.gz
   ```
   Recipients extract with: `gunzip tournament.html.gz`

3. **ZIP Archive**
   ```bash
   zip tournament.zip tournament.html
   ```

---

## Troubleshooting

### Standings Not Updating
- Verify all team names match exactly across `groups` and `groupMatches`
- Check that result IDs match match IDs in `groupMatches`
- Ensure scores are numbers (0, 1, 2, etc.)

### Knockout Bracket Shows "TBD"
- Verify group matches are entered with scores
- Check that knockout team references match group structure (e.g., "Group A 1st")
- Ensure team names in groups match exactly

### Results Not Persisting
- Verify browser allows localStorage
- Check browser's privacy settings
- Try in a different browser
- Clear browser cache if experiencing issues

### Mobile Layout Broken
- Check that CSS media queries are intact
- Verify no custom CSS overrides are breaking responsive layout
- Test in Chrome DevTools mobile emulation

---

## Summary of Steps

1. ✓ Copy world-cup-2026.html as template
2. ✓ Update tournament name, dates, and logo
3. ✓ Define all teams and groups
4. ✓ Add complete match schedule
5. ✓ Add stadium and venue information
6. ✓ Add team flag URLs/emojis
7. ✓ Configure broadcast channels
8. ✓ Define knockout bracket structure
9. ✓ Customize colors (optional)
10. ✓ Test all functionality
11. ✓ Compress and share

---

## Example: Converting for Olympics

For the Olympics, you would:
1. Change groups to "Medal Rounds" or "Divisions"
2. Update teams to individual athletes or countries
3. Change point system (medals instead: Gold=3, Silver=1, Bronze=0)
4. Adjust knockout bracket for tournament structure
5. Update venue names to Olympic venues

The framework is flexible enough for any tournament type!

---

## Support

- For HTML/CSS issues: Check browser console (F12 → Console tab)
- For logic issues: Add console.log() statements in JavaScript functions
- For data issues: Verify spelling and format consistency
- Export results for backup before major changes

Created with ❤️ by Marc Saunders and Claude
