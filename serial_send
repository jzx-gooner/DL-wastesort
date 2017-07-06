import serial
#compost_list=[]
#landfill_list=[]
#recycle_list=[]
#battery_list=[]

#if input is in compost_list:
	#return x='compost'

ser= serial.Serial('/dev/ttyUSB0',9600,8)

while(True):
	x=raw_input('input 1,2,3 or end')
	
	ser.write(x)
	
	if x=='end':
		break;
	
ser.close()
