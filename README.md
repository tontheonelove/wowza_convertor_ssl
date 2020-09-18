# wowza_convertor_ssl




Install certbot
#apt-get install certbot -y

Get New SSL
#certbot certonly --standalone


Check ssl 
#stat /etc/letsencrypt/live/yourdomain/fullchain.pem


crontab -e

#add these 2 lines

@weekly root cd /opt/letsencrypt && git pull >> /var/log/letsencrypt/letsencrypt-auto-update.log
@monthly root /opt/letsencrypt/letsencrypt-auto certonly --quiet --standalone --renew-by-default -d yourdomain >> /var/log/letsencrypt/letsencrypt-auto-update.log


#cd /usr/local/WowzaStreamingEngine/lib 

#wget https://github.com/robymus/wowza-letsencrypt-converter/releases/download/v0.1/wowza-letsencrypt-converter-0.1.jar

#cd /usr/local/WowzaStreamingEngine/lib

#java -jar wowza-letsencrypt-converter-0.1.jar -v /usr/local/WowzaStreamingEngine/conf/ /etc/letsencrypt/live/


#nano /usr/local/WowzaStreamingEngine/conf/VHost.xml

#### Edit Line ####

<KeyStorePath>${com.wowza.wms.context.VHostConfigHome}/conf/yourdomain.jks</KeyStorePath>
<KeyStorePassword>secret</KeyStorePassword>


service WowzaStreamingEngine restart



