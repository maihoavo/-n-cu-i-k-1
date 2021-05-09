# -n-cu-i-k-1
#Tạo danh sách điểm giữa kỳ, điểm cuối kỳ
diemgiuaky = []
diemcuoiky = []
diemketthuchp = []
#tạo danh sách môn học môn học 
m = ["Toán cao cấp", "Tiếng anh 1", "Dịch vụ hành chính", "Lập trình", "Công nghệ thông tin"]

#Hàm in tín chỉ, gọi hàm random
import random
def tinchi():
    list_tc = []
    total = 0
    while True: # xét điều kiện tổng số tín chỉ phải lớn hơn hoặc bằng 10
        for i in range(5):
            tinchi = random.randint(1, 3)
            total += tinchi
            list_tc.append(tinchi)
        if(total>=10):
            return list_tc
            break
        else:
            list_tc = []
            continue        
v = tinchi()
#Hàm nhập điểm thi giữa kỳ - điểm 30%   
def diem30():
    print("---Mời nhập điểm giữa kỳ---")
    for k in range(5):
        while True: # xét điều kiện để điểm nhập vào là hợp lý
            d30 = float(input("Môn " + m[k]) )
            if(d30 < 0 or d30 > 10):
                print("\nĐiểm bạn nhập không đúng","\n---Vui lòng nhập lại---")
                continue
            else:
                diemgiuaky.append(d30)
                break
    return diemgiuaky

#Hàm nhập điểm thi cuối kỳ - điểm 70 % 
def diem70():
    print("---Mời nhập điểm cuối kỳ---")
    for j in range(5):
        while True: #Xét điều kiện để điểm nhập vào là hợp lệ
            d70 = float(input("Môn " + m[j]) )
            if(d70 < 0 or d70 > 10):
                print("\nĐiểm bạn nhập không đúng","\n---Vui lòng nhập lại---")
                continue
            else:
                diemcuoiky.append(d70)
                break
    return diemcuoiky
#
d30 = tuple(diem30())
d70 = tuple(diem70())

a,b,c,e,f = d30
g,h,i,k,j = d70

#Hàm tính điểm kết thúc học phần
def tinh(d1,d2):
    diemketthuchp = (d1 * (30/100)) + (d2 * (70/100))
    return round(diemketthuchp, 2)
#hàm kiểm tra 
def dk(d1,d2):
    if (tinh(d1,d2) >= 5):
        return 'Qua môn'
    else:
        return 'Rớt'
row_0 = ' {:^115} '.format("BẢNG KẾT QUẢ HỌC TẬP")
row_1 = '+ {:-^4} + {:-^25} + {:-^10} + {:-^15} + {:-^15} + {:-^20} + {:->8} +'.format('', '', '','','','','')
row_2 = '| {:^4} | {:^25} | {:^10} | {:^15} | {:^15} | {:^20} | {:>8} |'.format('STT','Môn học', 'Tín chỉ', 'Điểm 30%','Điểm 70%','Điểm kết thúc HP','Kết quả')
row_3 = '+ {:-^4} + {:-^25} + {:-^10} + {:-^15} + {:-^15} + {:-^20} + {:->8} +'.format('', '', '','','','','')
row_4 = '| {:^4} | {:<25} | {:^10} | {:^15} | {:^15} | {:^20} | {:^8} |'.format('1',m[0],v[0], a,g,tinh(a,g),dk(a,g))
row_5 = '| {:^4} | {:<25} | {:^10} | {:^15} | {:^15} | {:^20} | {:^8} |'.format('2',m[1],v[1],b,h,tinh(b,h),dk(b,h))
row_6 = '| {:^4} | {:<25} | {:^10} | {:^15} | {:^15} | {:^20} | {:^8} |'.format('3',m[2],v[2],c,i,tinh(c,i),dk(c,i))
row_7 = '| {:^4} | {:<25} | {:^10} | {:^15} | {:^15} | {:^20} | {:^8} |'.format('4',m[3],v[3],e,k,tinh(e,k),dk(e,k))
row_8 = '| {:^4} | {:<25} | {:^10} | {:^15} | {:^15} | {:^20} | {:^8} |'.format('5',m[4],v[4],f,j,tinh(f,j),dk(f,j))
row_9 = '+ {:-^4} + {:-^25} + {:-^10} + {:-^15} + {:-^15} + {:-^20} + {:->8} +'.format('', '', '','','','','')
l_rows = [row_0,row_1,row_2,row_3,row_4,row_5,row_6,row_7,row_8,row_9]

for i in range(len(l_rows)):
    print(l_rows[i])
