# Automatic Jobs

You can setup automatic jobs (they will be scheduled with MAD start)

## Job controller file

Create file `autocommands.json` in `file_path` (config.ini)

All contents of this file gets loaded with MAD start.

## autocommands.json content

```
[
	{
		"uniqueid": 123456,
		"redo": true,
		"algotype": "loop",
		"algovalue": 10,
		"startwithinit": true,
		"origins": "tv1",
		"job": "Readout Pogo Version",
		"redoonerror": true
	},
	{
		"uniqueid": 123457,
		"redo": true,
		"algotype": "daily",
		"algovalue": "21:00",
		"startwithinit": true,
		"origins": "tv5|tv6|tv7",
		"job": "Readout RGC Version",
		"redoonerror": false
	}
]
```

## Field description

- `uniqueid` == Unique Job id (if you want a unique id for later selects)
- `redo` == true: reschedule jobs after finish them - false: start job one time
- `algotype` == `daily`: do this job once a day - `loop`: loop the job every x minutes
- `algovalue` == depends on algotype. `daily`: set time like "21:30" (24h format!) - `loop`: set loop time in minutes (120 = every 2 hours)
- `startwithinit` == `true`: start the job after init - `false`: start job according to planning
- `origins` == Single or list of devices (separated by pipe | )
- `job` == Name of job
- `redoonerror` == Reschedule jobs after getting an error


