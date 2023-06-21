create table bundesliga (
"date" text,
HomeTeam varchar,
AwayTeam varchar,
FTHG int,
FTAG int,
FTR varchar,
HTHG int,
HTAG int,
HTR varchar,
HS int,
"AS" int,
HST	int,
AST	int,
HF	int,
AF	int,
HC	int,
AC	int,
HY	int,
AY	int,
HR	int,
AR int);


select * from bundesliga;

create table premier_league (
"date" text,
HomeTeam varchar,
AwayTeam varchar,
FTHG int,
FTAG int,
FTR varchar,
HTHG int,
HTAG int,
HTR varchar,
referee varchar,
HS int,
"AS"	int,
HST	int,
AST	int,
HF	int,
AF	int,
HC	int,
AC	int,
HY	int,
AY	int,
HR	int,
AR int
);



with  win_b as (select 
(case 
	when ftr = 'A' then awayteam
	when ftr = 'H' then hometeam
	when ftr = 'D' then NULL
end) as winner,
(case 
	when to_date("date", 'DD/MM/YY') >= to_date('15.08.08', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('23.05.09', 'DD.MM.YY') then '08/09'
	when to_date("date", 'DD/MM/YY') >= to_date('07.08.09', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('08.05.10', 'DD.MM.YY') then '09/10'
	when to_date("date", 'DD/MM/YY') >= to_date('20.08.10', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('14.05.11', 'DD.MM.YY') then '10/11'
	when to_date("date", 'DD/MM/YY') >= to_date('05.08.11', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('05.05.12', 'DD.MM.YY') then '11/12'
	when to_date("date", 'DD/MM/YY') >= to_date('24.08.12', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('18.05.13', 'DD.MM.YY') then '12/13'
	when to_date("date", 'DD/MM/YY') >= to_date('09.08.13', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('10.05.14', 'DD.MM.YY') then '13/14'	
	when to_date("date", 'DD/MM/YY') >= to_date('22.08.14', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('23.05.15', 'DD.MM.YY') then '14/15'
	when to_date("date", 'DD/MM/YY') >= to_date('14.08.15', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('14.05.16', 'DD.MM.YY') then '15/16'
	when to_date("date", 'DD/MM/YY') >= to_date('26.08.16', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('20.05.17', 'DD.MM.YY') then '16/17'
	when to_date("date", 'DD/MM/YY') >= to_date('18.08.17', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('12.05.18', 'DD.MM.YY') then '17/18'
	when to_date("date", 'DD/MM/YY') >= to_date('24.08.18', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('23.12.18', 'DD.MM.YY') then '18/19'	
end) as season
from bundesliga
),
stat_b as(
select season, winner, count(*) as Wins_Bundesliga
from win_b
where winner is not null and season is not null
group by season, winner
),
win_p as(
select 
(case 
	when ftr = 'A' then awayteam
	when ftr = 'H' then hometeam
	when ftr = 'D' then NULL
end) as winner,
(case 
	when to_date("date", 'DD/MM/YY') >= to_date('15.08.09', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('09.05.10', 'DD.MM.YY') then '09/10'
	when to_date("date", 'DD/MM/YY') >= to_date('14.08.10', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('22.05.11', 'DD.MM.YY') then '10/11'
	when to_date("date", 'DD/MM/YY') >= to_date('13.08.11', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('13.05.12', 'DD.MM.YY') then '11/12'
	when to_date("date", 'DD/MM/YY') >= to_date('18.08.12', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('19.05.13', 'DD.MM.YY') then '12/13'
	when to_date("date", 'DD/MM/YY') >= to_date('17.08.13', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('11.05.14', 'DD.MM.YY') then '13/14'	
	when to_date("date", 'DD/MM/YY') >= to_date('16.08.14', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('24.05.15', 'DD.MM.YY') then '14/15'
	when to_date("date", 'DD/MM/YY') >= to_date('08.08.15', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('17.05.16', 'DD.MM.YY') then '15/16'
	when to_date("date", 'DD/MM/YY') >= to_date('13.08.16', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('21.05.17', 'DD.MM.YY') then '16/17'
	when to_date("date", 'DD/MM/YY') >= to_date('11.08.17', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('13.05.18', 'DD.MM.YY') then '17/18'
	when to_date("date", 'DD/MM/YY') >= to_date('10.08.18', 'DD.MM.YY') and to_date("date", 'DD/MM/YY') <= to_date('03.01.19', 'DD.MM.YY') then '18/19'	
end) as season
from premier_league),
stat_p as(
select season, winner, count(*) as Wins_Premier_league
from win_p
where winner is not null and season is not null
group by season, winner
)
select coalesce(b.season, p.season) as season, coalesce(b.winner, p.winner) as winner, coalesce(wins_bundesliga, 0) as wins_bundesliga, coalesce(wins_premier_league, 0) as wins_premier_league
from stat_b b
full join stat_p p on p.season = b.season and p.winner = b.winner
order by 1, 2;
