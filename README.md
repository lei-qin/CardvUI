# zkgui_sample
A gui sample which set up with Flythings IDE.

# flythings��ʹ�òο���

1��Ŀ¼˵��

	app����������zkgui�����ڼ���flythings��UI���ɵ�so
	customer_zk��Ŀǰ�����Ѿ����Թ��Ĵ��������Ҫ�����ݣ����������Ŀ¼�ο���
	/project/image/configs/i2m/rootfs_fastboot.mk
	SSD_sample��Flythings IDE����Ĺ��̣�����libzkgui.so
	tool���޸��������õĴ������ķ���

2������app��

	����app���޸�makefile��������Ҫ�޸ģ�
	PROJECT_PATH��ֵ��Ӧ��·��,��·����Ҫ��SDK��project·��һ�¡�
	PROJECT_PATH=/home/beal.wu/i2m_i6_master/project
	�޸���ɺ�make���ɣ���bin������zkgui�������滻/customer_zk/bin�����zkgui
	
3������SSD_sample��

	��Flythings��IDE��Ȼ���빤�̣�����ο���IDEʹ�òο�.pdf������Flythings����ʹ��ָ��.pdf��
	�������ɵ�libzkgui.so�����滻customer_zk/lib���������
	��Ҫ����wifi���ܣ��ɽ�jni/Makefile�е�CONFIG_WLAN_SWITCH��Ϊenable��Ȼ�����±���libzkgui.so���ɡ�
	
4��������¼����

	cd /project
	./setup_config.sh configs/nvr/i2m/8.2.1/nor.glibc-ramfs.011a.64
	make clean;make image
	
	��ʵ��һ����Ҫ�����config�����룬ֻҪ���н�customer_zk��������ݷ��ö�Ӧ��Ŀ¼���ɡ�

ע��1024*600����800*480�ĳ���

	1����Ҫ��TP�ĳ�800*480
	2��fbdev.ini������Ϊ800*480
	3��zkgui����ͷ�ļ�Ϊ1024*600
	4�������Ļ���disp����ʵ�ʵ�1024*600����UI����GOP1������800*480��UI���浽1024*600������


# SSD_PLAYER
Ssplaer base on SSD UI

IDE:
	����ZK UI��������IDE��
	���뷽����
		1.ʹ��FlyThings IDE����IDE���̣�
		2.ѡ����Ŀ������Ҽ�ѡ�������Ŀ��������Ŀ��
		3.������޸�UI��Դ��ز��֣���Ҫ��������Ŀ���ui�ļ����滻��customer_zk\res
		
app:
	����������app������call��IDE�б��������so
	���뷽����
		1.������Ҫ���panel�޸�sstardisp.c�򿪶�Ӧ�����ã�
			#define UI_1024_600 1
		2.make clean;make����
		
customer_zk:
	��������������app�Ļ���
	1.��IDE����õ�IDE\libs\armeabi\libzkgui.so�滻��customer_zk\lib
	2.����Ҫ��ffmpeg lib������customer_zk\lib
	
tool:
	�����ı䴥���ֱ������õ��ļ���
	echo 1024x600.bin > /sys/bus/i2c/devices/1-005d/gtcfg
	echo 800x480.bin > /sys/bus/i2c/devices/1-005d/gtcfg

���в�������
	1.��app���������zkgui copy��customer������
	2.��customer_zk��res��lib copy��customer������
	3.��customer_zk��etc������ļ�����������/etc���棻
	4.cd /customer/lib,ִ�У�export LD_LIBRARY_PATH=/lib:$PWD:$LD_LIBRARY_PATH
	5.����zkgui: ./zkgui
	
	ע�����û�����������ǹ��ŵ�gpioû�����ߣ����Բο����²������ߣ�
	1. cd /sys/class/gpio/
	2. echo 12 > export
	3. echo out > direction
	4. echo 1 > value


