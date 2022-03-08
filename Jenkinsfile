pipeline {
  agent any
  stages {
    stage('buildS1022') {
      steps {
        sh '''export BS=10.194.8.47
export LTES=172.17.0.3
export psswd=123456


if [ -f "/var/jenkins_home/LTE_CrontabLog.log" ] ; then
    rm /var/jenkins_home/LTE_CrontabLog.log
fi

#sshpass -p "123456" ssh dailybuild@$BS "sshpass -p 123456 ssh $LTES \\"/home/dailybuild/disk2/DailyBuild/LTE_Daily_build.bash f=LTE_build_list.tmp n=1\\""  > /var/jenkins_home/LTE_CrontabLog.log

if [ -f "/var/jenkins_home/LTE_CrontabLog.log" ] ; then
    date >> /var/jenkins_home/LTE_CrontabLog.log
    sshpass -p "fred1127" scp /var/jenkins_home/LTE_CrontabLog.log fred_tseng@10.194.10.188:/home/fred_tseng/log/LTE_CrontabLog.Jenkins.log
fi


if [ -f "/var/jenkins_home/Fota_CrontabLog.log" ] ; then
    rm /var/jenkins_home/Fota_CrontabLog.log
fi

sshpass -p "123456" ssh dailybuild@$BS "sshpass -p 123456 ssh $LTES \\"bash /home/dailybuild/disk2/DailyBuild/all_fota_pack.sh f=LTE_build_list.tmp n=1\\""  > /var/jenkins_home/Fota_CrontabLog.log

if [ -f "/var/jenkins_home/Fota_CrontabLog.log" ] ; then
    date >> /var/jenkins_home/Fota_CrontabLog.log
    sshpass -p "fred1127" scp /var/jenkins_home/Fota_CrontabLog.log fred_tseng@10.194.10.188:/home/fred_tseng/log/Fota_CrontabLog.Jenkins.log
fi

'''
        mail(subject: 'BlueOceanDailybuildS1022V01', body: 'as title', to: 'fred_tseng@askey.com')
      }
    }

  }
}