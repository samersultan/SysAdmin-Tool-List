To get list of all computers with last time accessed

    get-adcomputer -filter * -properties passwordlastset | select name, passwordlastset | sort passwordlastset
