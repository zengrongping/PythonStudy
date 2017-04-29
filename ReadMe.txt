comment= 'D:/zeng/week2 Python基础语言讲解/作业/太空旅客1.txt'
a1 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/角色/反派.txt'
a2 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/角色/角色.txt'
a3 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/角色/角色中的其他.txt'
a4 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/角色/男主角.txt'
a5 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/角色/女主角.txt'
a6 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/角色/配角.txt'
a7 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/剧情/发展.txt'
a8 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/剧情/结局.txt'
a9 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/剧情/剧情.txt'
a10 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/剧情/开头.txt'
a11 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/剧情/泪点.txt'
a12 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/剧情/笑点.txt'
a13 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/视听/动作.txt'
a14 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/视听/画面.txt'
a15 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/视听/镜头.txt'
a16 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/视听/试听效果中的其他.txt'
a17 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/视听/视听.txt'
a18 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/视听/音乐.txt'
a19 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/制作/编剧.txt'
a20 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/制作/出品公司.txt'
a21 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/制作/导演.txt'
a22 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/制作/选景.txt'
a23 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/制作/制作.txt'
a24 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/主题/风格.txt'
a25 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/主题/题材内容.txt'
a26 = 'D:/zeng/week2 Python基础语言讲解/作业/词典/主题/主题.txt'

def FindAWord(str1, str2):  # 词语匹配简易版--- 2个字符重合视为有该类型评价出现    str1:查找库  str:被查找
    a = 0
    b = 2
    str3 = ''
    while b <= len(str2):
        str3 = str2[a:b]
        if str1.find(str3) != -1:
            return 1
        else:
            a = a + 1
            b = b + 1
    return 0
    dic = open(s2,'r')
    if (FindAWord(dic, str1) == 'success'):
        #print('this word can be found in this dictionary')
        return 1
    return 0

A = [a1,a2,a3,a4,a5,a6,a7,a8,a9,a10,a11,a12,a13,a14,a15,a16,a17,a18,a19,a20,a21,a22,a23,a24,a25,a26]
B =[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0] #B: 每一个关注点出现的次数
C =['角色-反派','角色-角色','角色-角色中的其他','角色-男主角','角色-女主角','角色-配角',
    '剧情-发展','剧情-结局','剧情-剧情','剧情-开头','剧情-泪点','剧情-笑点',
    '视听-动作','视听-画面','视听-镜头','视听-视听效果中的其他','视听-视听','视听-音乐',
    '制作-编剧','制作-出品公司','制作-导演','制作-选景','制作-制作',
    '主题-风格','主题-题材内容','主题-主题']
j = 0 #j:出现标注词的次数
file = open(comment,'r', encoding='UTF-8')
for line in file.readlines():
    for i in range(26):
        dic = open(A[i], 'r', encoding='UTF-8')
        text = dic.read()
        j = j + FindAWord(line,text )
        B[i] = B[i] + FindAWord(line, text)
print(j)
for i in range(26):
    print ('对',C[i],'的关注度为',B[i]/j*100,'%')
