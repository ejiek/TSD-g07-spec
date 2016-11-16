# Alerts Data Inegrity

Separate DB for storing backup. In addition to the existing alert structure CRC is introduced. CRC is computed on the first writing to the DB and stored alongside with message. On every access to the alert CRC is computed again and compared to the existing one. In case both CRCs are equal alert data is returned. In case CRCs are not equal this alert looked up in the backup. In case backup contains this alert and CRC of backups message is equal to the CRC stored in backup this alert data is returned to the user and written to the main DB. 

Backup is formed in iterative way: once it is created we only add new chunks of information. "New" is defined by the id of alert: alert is new when its id is greater than the last ine in back up.

# Ноspitаl Сооrdination Prоblеm
To resolve this problem coordinator will have opportunity to determine how many people have injured in a crisis by making note in the new column in table CRISIS.

![casualtyControl](https://github.com/ejiek/TSD-g07-spec/blob/master/casualtyControl.png) ![injuryControl](https://github.com/ejiek/TSD-g07-spec/blob/master/injuryControl.png)

From now system has new actor - casualty. Casualty is a person, who have injured in an accident. Every casualty have some (one, two or more) injuries with its own type. Injured people compose casualty list of crisis. Coordinator compile this list by himself.

![err](https://github.com/ejiek/TSD-g07-spec/blob/master/err.png)

This list will be associated with crisis and stored in new DB tables CASUALTY and INJURES like records about victims, their injuries and their cause. In that way we have list, which contains all crises (table CRISIS) and new panel, where hospitals can see crises with victims.
Hospital is a person, who have access (by authentication) to his own hospital (in which he works) panel. Hospital panel contains information about crysis.
Every crisis has casualty list, which contains information about their injuries:
* Part of Body
* Type of injury
* Cause of injury

Hospital coordinator can see how many people (with their injuries) are going to get help in his hospital.

![crisisList](https://github.com/ejiek/TSD-g07-spec/blob/master/pics/crisisList.png)
![InjuryList](https://github.com/ejiek/TSD-g07-spec/blob/master/pics/InjuryList.png)
![partsOfBody](https://github.com/ejiek/TSD-g07-spec/blob/master/pics/partsOfBody.png)
![typeOfInjury](https://github.com/ejiek/TSD-g07-spec/blob/master/pics/typeOfInjury.png)
![causeOfInjury](https://github.com/ejiek/TSD-g07-spec/blob/master/pics/causeOfInjury.png)
