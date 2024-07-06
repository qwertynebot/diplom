timeout=90
counter=0
until /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P 'Qwerty-1' -d master -Q "SELECT 1" &>/dev/null || [ $counter -gt $timeout ]
do
    sleep 1
    ((counter++))
done

if [ $counter -gt $timeout ]; then
    echo "Помилка: Не вдалося підключитися до SQL Server протягом $timeout секунд."
    exit 1
fi

/opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P 'Qwerty-1' -d master -i setup.sql