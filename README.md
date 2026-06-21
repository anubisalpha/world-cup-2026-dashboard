# World Cup 2026 Dashboard

A fully-featured, self-contained interactive tournament tracking dashboard for the FIFA World Cup 2026. No build tools. No external dependencies. Just one HTML file with everything you need to follow the entire tournament in real-time.

## Overview

This dashboard provides a complete tracking experience for the World Cup 2026, from the group stage through to the final match. Every match, team, stadium, and broadcast channel is pre-configured and ready to use. Update match results as games are played, and watch the tournament unfold dynamically before your eyes.

## Features

### 📊 Group Stage Management

- **Scroll to Today**: The group stage view automatically scrolls to today's matches on load and when switching tabs

- **Complete Schedule**: All 48 group stage matches pre-loaded with:
  - Exact match dates and times
  - Venue information and stadium details
  - All 12 groups (A through L) with 4 teams each
  - Live broadcast channel information for UK viewers (BBC, ITV, etc.)

- **Live Result Entry**: Intuitive match result editor allowing you to:
  - Enter team goals for any group stage match
  - See results reflected immediately across the dashboard
  - Update results at any time as matches are replayed or corrected

- **Automatic Point Calculation**: The dashboard applies FIFA's standard scoring system automatically:
  - 3 points for a win
  - 1 point for a draw
  - 0 points for a loss

- **Dynamic Group Standings**: Watch group tables update in real-time as you enter results:
  - Auto-sorted by points (descending)
  - Goal difference as the primary tiebreaker
  - Goals scored as the secondary tiebreaker
  - Visual ranking from 1st to 4th place in each group

### 🏆 Knockout Stage Management

- **Dynamic Bracket Generation**: The knockout bracket automatically populates based on group results:
  - Quarter-finals (8 matches) with 1st vs 2nd from paired groups
  - Semi-finals (4 matches) with winners advancing automatically
  - Final (1 match) with the last two teams standing
  - All team qualifications calculated recursively from group standings

- **Third-Place Playoff**: Conditional tracking of the match for 3rd place:
  - Only enabled after semi-final results are entered
  - Automatically identifies the losing semi-finalists
  - Tracks third-place winner separately

- **Knockout Result Entry**: Simple interface to record knockout match winners and advance teams through the bracket

### 🌐 Global Coverage

- **Stadium Information**: Comprehensive details for every stadium hosting matches:
  - Stadium capacity
  - City and venue location
  - Interactive hover tooltips with full information
  - Direct links to official FIFA stadium pages

- **Team Information**: Direct links for every national team:
  - FIFA official pages for each team
  - Maintained throughout group stage and knockout rounds

- **UK Broadcast Channels**: Pre-configured channel mappings with direct links:
  - BBC matches
  - ITV matches
  - All channels organized and linkable for easy access to live streams

### 💾 Data Management

- **Export Functionality**: Save your tournament progress at any time:
  - Full tournament state exported as JSON
  - Includes all match results, group standings, and knockout progress
  - Perfect for backup or sharing with others

- **Import Functionality**: Load a previously saved tournament state:
  - Restore from a JSON export
  - Seamlessly continue tracking from where you left off
  - Easy sharing of tournament state with friends

- **Import Online**: One-click import of the latest results from GitHub:
  - Fetches the most recent results export from the repository
  - No need to manually download and import JSON files
  - Keeps your scores up to date with a single button press

- **Local Storage**: All data persists in your browser:
  - Automatic saving to browser localStorage
  - No internet connection needed to view or update results (after initial load)
  - Data survives browser refresh and restarts

### 🔄 Auto-Update

- **Version Detection**: The dashboard checks GitHub for newer versions on load
- **Update Banner**: A visible notification appears in the header when an update is available
- **Version Label**: Current version number and build date always visible in the header for quick reference

### 📱 Responsive Design

- **Desktop Experience**: Full-width optimized layout with all features visible at once
- **Tablet Experience**: Adapted spacing and touch-friendly interface
- **Mobile Experience**: Vertical layout with collapsible sections for easy navigation on phones

### 🎨 Professional Presentation

- **FIFA Branding**: Official FIFA World Cup 2026 logo and styling
- **Clean Interface**: Intuitive layout organized by tournament stage
- **Creator Attribution**: Built-in credit display and contact information
- **Feature Showcase**: In-app feature list for quick reference

## How to Use

### Getting Started

1. Open `world-cup-2026.html` in any modern web browser
2. The entire tournament schedule is pre-loaded and ready to go
3. No installation, setup, or login required

### Entering Results

1. **Group Stage Results**: Click on any group stage match and enter the goals scored by each team
2. **Group Standings**: Watch the group tables automatically update with points and rankings
3. **Knockout Stage**: Once group stage is complete, the knockout bracket populates with qualified teams
4. **Knockout Results**: Enter winners to advance teams through quarters, semis, and final

### Managing Tiebreakers

- The dashboard automatically sorts groups by points, goal difference, and goals scored
- For true ties (same points, GD, and GF), you can manually resolve the order:
  - A "Resolve Tiebreaker" button appears after all 3 group matches are entered
  - Drag and drop to reorder tied teams
  - The knockout bracket updates instantly based on your resolution

### Saving and Sharing

- **Export**: Click "Export Tournament" to download your progress as a JSON file
- **Import**: Click "Import Tournament" and select a previously saved JSON file to restore your state
- **Share**: Email the exported JSON to friends so they can view your tournament progress

## Technical Details

### Architecture

- **Single HTML File**: No build process, no bundling, no complexity
- **Pure JavaScript**: Vanilla JS with no framework dependencies
- **Embedded Data**: All tournament data, venues, teams, and channels built into the HTML
- **Client-Side Processing**: Everything runs locally in your browser for instant updates

### Data Structure

```
- 12 Groups (A-L) with 4 teams each
- 48 Group Stage Matches
  - Date, time, stadium, location, UK broadcast channel
- 25 Knockout Matches
  - Quarter-finals: 8 matches
  - Semi-finals: 4 matches
  - Final: 1 match
  - Third-place playoff: 1 match
- 32 National Teams with FIFA page links
- 12 Stadiums with capacities and locations
- Broadcast channel mappings with stream links
```

### Browser Compatibility

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Any modern browser with ES6 support and localStorage

## Customization Guide

This dashboard is built to be customizable for any tournament format. The same framework can be adapted for:

- **UEFA Euro** (16 teams, 4 groups)
- **Copa América** (10 teams, 2 groups)
- **African Cup of Nations** (24 teams, 6 groups)
- **Olympics** (Football tournament)
- **Custom Tournaments** of any size and format

All data is embedded in a single data structure at the top of the HTML file. Edit groups, teams, stadiums, matches, and channels directly in the code to adapt for other tournaments.

## File Size

- **Single file**: ~106 KB (html, css, javascript, all data embedded)
- **Compressed**: ~16 KB when gzipped (recommended for email sharing)

## Distribution

The single HTML file can be:
- Opened directly in a browser from your computer
- Emailed to friends or colleagues
- Hosted on any web server
- Saved locally and shared via cloud storage
- No server backend required

## License

Created for the 2026 FIFA World Cup. Freely shareable and customizable for personal use.

## Support

For questions, feedback, or customization requests for other tournaments, please reach out to the creator.

---

**Ready to track the 2026 World Cup?** Open `world-cup-2026.html` in your browser and start entering match results!

---

## ☕ By the way...

If you find this dashboard useful, consider [buying me a coffee](https://buymeacoffee.com/anubisalpha). No pressure at all — but if you'd like to support the project, it's genuinely appreciated.
