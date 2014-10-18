Initd - Basic Skeleton
----------------------

```shell
SELENIUM_HOME="/var/lib/selenium/selenium-server-standalone-2.25.0.jar"
SELENIUM_PORT="5555"
SELENIUM_LOG="/var/log/selenium/selenium-output.log"
SELENIUM_ERROR_LOG="/var/log/selenium/selenium-error.log"
SELENIUM_PID_FILE="/tmp/selenium.pid"

case "${1:-''}" in
        'start')
                if test -f $SELENIUM_PID_FILE
                then
                        echo "Selenium is already running."
                else
                        java -jar ${SELENIUM_HOME} -port ${SELENIUM_PORT} > ${SELENIUM_LOG} 2> ${SELENIUM_ERROR_LOG} & echo $! > ${SELENIUM_PID_FILE}
                        echo "Starting Selenium..."

                        error=$?
                        if test $error -gt 0
                        then
                                echo "Couldn't start Selenium!"
                        fi
                fi
        ;;
        'stop')
                if test -f $SELENIUM_PID_FILE
                then
                        echo "Stopping Selenium..."
                        PID=`cat $SELENIUM_PID_FILE`
                        kill -3 $PID
                        if kill -9 $PID ;
                                then
                                        sleep 2
                                        test -f $SELENIUM_PID_FILE && rm -f $SELENIUM_PID_FILE
                                else
                                        echo "Selenium could not be stopped..."
                                fi
                else
                        echo "Selenium is not running."
                fi
                ;;
        'restart')
                if test -f $SELENIUM_PID_FILE
                then
                        kill -HUP `cat $SELENIUM_PID_FILE`
                        test -f $SELENIUM_PID_FILE && rm -f $SELENIUM_PID_FILE
                        sleep 1
                        java -jar ${SELENIUM_HOME} -port ${SELENIUM_PORT} > ${SELENIUM_LOG} 2> ${SELENIUM_ERROR_LOG} & echo $! > ${SELENIUM_PID_FILE}
                        echo "Reload Selenium..."
                else
                        echo "Selenium isn't running..."
                fi
                ;;
	'status')
		if test -f $SELENIUM_PID_FILE
		then
			echo "Selenium is running..."
		else
			echo "Selenium is stopped"
		fi
		;;
	*)      # no parameter specified
                echo "Usage: $SELF start|stop|restart|status"
                exit 1
        ;;
esac
```

