import nflgame

year = 2017
week = 17
kind = 'REG'


past_games = nflgame.games(year=year, week=week, kind=kind)
for game in past_games:
    print game

print '-'

future_games = [game for game in nflgame.live._games_in_week(year=year, week=week, kind=kind) if game['eid'] not in [g.eid for g in past_games]]
for game in future_games:
    print '{} at {} on {}/{} {}'.format(game['away'], game['home'], game['month'], game['day'], game['time'])