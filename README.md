import pynvml, platform, psutil, time

#not accurate prices

pynvml.nvmlInit()

nogpu = False
noram = False


def getgpu():
    handle = pynvml.nvmlDeviceGetHandleByIndex(0)
    gpu_name = pynvml.nvmlDeviceGetName(handle)
    print("GPU Name:", gpu_name)

def getcpu():
    cpu_name = platform.processor()
    print("CPU Name:", cpu_name)

def getram():
    total_memorybyte = psutil.virtual_memory().total
    total_memory = total_memorybyte / 1073741824
    print("Total Memory:", total_memory, "gigabytes")

def get_motherboard_info():
    motherboard_info = platform.node()
    return motherboard_info

def getmotherboard():
    motherboard_info = get_motherboard_info()
    print("Motherboard:", motherboard_info)


print("CODE WRITTEN BY YL77, PRICE NOT ALWAYS ACCURATE, ERRORS MAY ENSUE IF COMPONENTS NOT FOUND AND DOESN'T CALCULATE ALL COMPONENTS LIKE SSD, HDD, PSU ETC.")
time.sleep(2)
ready = input("Do you want to know the estimated price of your operating system? (yes or no)").lower()
if ready == "no":
    print("Execute code when you're ready!")
    quit()
elif ready == "yes":
    getgpu()
    getcpu()
    getram()
    getmotherboard()
else:
    print("invalid argument try again")
    quit()

print("note, calculating every component price is very challenging as it's statically typed. You can search up individual price on the web if the program gets any wrong.")
time.sleep(2)

price_calculation = 0

ram = total_memorybyte = psutil.virtual_memory().total
ram1 = ram / 1073741824
if ram1 <= 1:
    price_calculation += 10
elif ram1 <= 2:
    price_calculation += 20
elif ram1 <= 4:
    price_calculation += 40
elif ram1 <= 8:
    price_calculation += 60
elif ram1 <= 16:
    price_calculation += 100
elif ram1 <= 32:
    price_calculation += 180
elif ram1 <= 64:
    price_calculation += 350
elif ram1 <= 128:
    price_calculation += 600
elif ram1 <= 256:
    price_calculation += 1200
elif ram1 >= 300:
    price_calculation += 2000
else:
      noram = True

human_input = input("is your GPU a NVIDIA ti? yes/no")
if human_input == "no":
    pass
elif human_input == "yes":
    price_calculation += 150
else:
    print("invalid input")
    

handle1 = pynvml.nvmlDeviceGetHandleByIndex(0)
gpucalc = pynvml.nvmlDeviceGetName(handle1).decode('utf-8')
if "GeForce" in gpucalc:
    gpucalc = gpucalc.split("GeForce ")[1].split("M")[0]

if gpucalc == "GTX 690":
        price_calculation += 200
elif gpucalc == "GTX 670":
        price_calculation += 90
elif gpucalc == "GTX 680":
        price_calculation += 150
elif gpucalc == "GTX 770":
        price_calculation += 120
elif gpucalc == "GTX 780":
        price_calculation += 150
elif gpucalc == "GTX 660":
        price_calculation += 80
elif gpucalc == "GTX 760":
        price_calculation += 100
elif gpucalc == "GTX 650":
        price_calculation += 50
elif gpucalc == "GTX 750":
        price_calculation += 70
elif gpucalc == "GTX 560":
        price_calculation += 60
elif gpucalc == "GTX 570":
        price_calculation += 90
elif gpucalc == "GTX 580":
        price_calculation += 100
elif gpucalc == "GTX 590":
        price_calculation += 120
elif gpucalc == "GTX 460":
        price_calculation += 40
elif gpucalc == "GTX 470":
        price_calculation += 70
elif gpucalc == "GTX 480":
        price_calculation += 80
elif gpucalc == "GTX 950":
        price_calculation += 60
elif gpucalc == "GTX 960":
        price_calculation += 80
elif gpucalc == "GTX 970":
        price_calculation += 100
elif gpucalc == "GTX 980":
        price_calculation += 120
elif gpucalc == "GTX 1050":
        price_calculation += 50
elif gpucalc == "GTX 1060":
        price_calculation += 90
elif gpucalc == "GTX 1070":
        price_calculation += 120
elif gpucalc == "GTX 1080":
        price_calculation += 150
elif gpucalc == "RTX 2060":
        price_calculation += 100
elif gpucalc == "RTX 2060 Super":
        price_calculation += 120
elif gpucalc == "RTX 2070":
        price_calculation += 150
elif gpucalc == "RTX 2070 Super":
        price_calculation += 150
elif gpucalc == "RTX 2080":
        price_calculation += 200
elif gpucalc == "RTX 2080 Super":
        price_calculation += 220
elif gpucalc == "RTX 3060":
        price_calculation += 100
elif gpucalc == "RTX 3070":
        price_calculation += 150
elif gpucalc == "RTX 3080":
        price_calculation += 200
elif gpucalc == "RTX 3090":
        price_calculation += 300
elif gpucalc == "RTX A4000":
        price_calculation += 180
elif gpucalc == "RTX A5000":
        price_calculation += 400
elif gpucalc == "RTX A6000":
        price_calculation += 800
else:
    print("could not find gpu")
    nogpu = True



print("FINAL EVALUATION:")
time.sleep(1.55)

if nogpu == True:
    print(f"Calculating only your ram your os is estimated to be: ${price_calculation} USD")
elif noram == True:
    print(f"Calculating only your ram your os is estimated to be: ${price_calculation} USD")
elif noram == True and nogpu == True:
    print("Nothing to evaluate")
else:
    print(f"Calculating your ram and your GPU your os is estimated to be worth: ${price_calculation} USD")

print("thanks for using os component calculation by yl77 I might revisit project and include more component calculations")
quit()













