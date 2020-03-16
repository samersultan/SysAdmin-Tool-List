To get list of all computers with last time accessed

    get-adcomputer -filter * -properties passwordlastset | select name, passwordlastset | sort passwordlastset
    
 
Remove older than 90 days:

    $date = (get-date).adddays(-90)

Then run


    get-adcomputer -filter {passwordlastset -lt $date} -properties passwordlastset | select name, passwordlastset | sort passwordlastset



And to clean up

    get-adcomputer -filter {passwordlastset -lt $date} -properties passwordlastset | remove-adobject -recursive -verbose -confirm:$false
