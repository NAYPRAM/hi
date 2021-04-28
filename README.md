
 gg.alert("ขอบคุณ 𝑪𝒉𝒆𝒂𝒕𝑨𝒄𝒕𝒊𝒐𝒏 ด้วยครับ\n\n\n กด ตกลงเพื่อเข้าสู่ระบบ")
function SearchWrite(Search, Write, Type)
  gg.clearResults()
  gg.setVisible(false)
  gg.searchNumber(Search[1][1], Type)
  local count = gg.getResultCount()
  local result = gg.getResults(count)
  gg.clearResults()
  local data = {} 
  local base = Search[1][2] 
  
if (count > 0) then
      for i, v in ipairs(result) do
          v.isUseful = true 
      end
      
      for k=2, #Search do
          local tmp = {}
          local offset = Search[k][2] - base 
          local num = Search[k][1] 
          
          for i, v in ipairs(result) do
              tmp[#tmp+1] = {} 
              tmp[#tmp].address = v.address + offset  
              tmp[#tmp].flags = v.flags  
          end
          
          tmp = gg.getValues(tmp) 
          
          for i, v in ipairs(tmp) do
              if ( tostring(v.value) ~= tostring(num) ) then 
                  result[i].isUseful = false 
              end
          end
      end

      for i, v in ipairs(result) do
          if (v.isUseful) then 
              data[#data+1] = v.address
          end
      end
      
      if (#data > 0) then
      
      local t = {}
      local base = Search[1][2]
      for i=1, #data do
          for k, w in ipairs(Write) do
              offset = w[2] - base
              t[#t+1] = {}
              t[#t].address = data[i] + offset
              t[#t].flags = Type
              t[#t].value = w[1]
              
              if (w[3] == true) then
                  local item = {}
                  item[#item+1] = t[#t]
                  item[#item].freeze = true
                  gg.addListItems(item)
              end
              
          end
      end
      gg.setValues(t)
  
      gg.addListItems(t)
      else
          gg.toast("ไม่มีข้อมูล", false)
          return false
      end
  else
      gg.toast("Not Found")
      return false
  end
end



function split(szFullString, szSeparator) local nFindStartIndex = 1 local nSplitIndex = 1 local nSplitArray = {} while true do local nFindLastIndex = string.find(szFullString, szSeparator, nFindStartIndex) if not nFindLastIndex then nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, string.len(szFullString)) break end nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, nFindLastIndex - 1) nFindStartIndex = nFindLastIndex + string.len(szSeparator) nSplitIndex = nSplitIndex + 1 end return nSplitArray end function xgxc(szpy, qmxg) for x = 1, #(qmxg) do xgpy = szpy + qmxg[x]["offset"] xglx = qmxg[x]["type"] xgsz = qmxg[x]["value"] gg.setValues({[1] = {address = xgpy, flags = xglx, value = xgsz}}) xgsl = xgsl + 1 end end function xqmnb(qmnb) gg.clearResults() gg.setRanges(qmnb[1]["memory"]) gg.searchNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "เปิด") else gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "เปิด") else sl = gg.getResults(999999) sz = gg.getResultCount() xgsl = 0 if sz > 999999 then sz = 999999 end for i = 1, sz do pdsz = true for v = 4, #(qmnb) do if pdsz == true then pysz = {} pysz[1] = {} pysz[1].address = sl[i].address + qmnb[v]["offset"] pysz[1].flags = qmnb[v]["type"] szpy = gg.getValues(pysz) pdpd = qmnb[v]["lv"] .. ";" .. szpy[1].value szpd = split(pdpd, ";") tzszpd = szpd[1] pyszpd = szpd[2] if tzszpd == pyszpd then pdjg = true pdsz = true else pdjg = false pdsz = false end end end if pdjg == true then szpy = sl[i].address xgxc(szpy, qmxg) xgjg = true end end if xgjg == true then gg.toast(qmnb[2]["name"] .. "เปิดสำเร็จ,เสร็จ" .. xgsl .. "ข้อมูล") else gg.toast(qmnb[2]["name"] .. "เปิด") end end end end
local jldz={}function KYXG(DZ,XGSJ,GNM,JLDZ)local t={}for i=1,#DZ do for k,w in ipairs(XGSJ) do offset=w[1]*4 t[#t+1]={}t[#t].address=DZ[i]+offset t[#t].flags=w[2]t[#t].value=w[3]if(w[4]==true)then local item={}item[#item+1]=t[#t]item[#item].freeze=true gg.addListItems(item)end end end gg.setValues(t)gg.toast(GNM.."เปิดสำเร็จ")end function KY_ZZ(NCLX,SSSJ,XGSJ,GNM)gg.setVisible(false)if jldz[NCLX[4]]==nil then gg.clearResults()gg.setRanges(NCLX[1])gg.searchNumber(NCLX[2],NCLX[3])local count=gg.getResultCount()local result=gg.getResults(count)gg.clearResults()local data={}if(count>0)then for i,v in ipairs(result) do v.isUseful=true end for k=1,#SSSJ do local tmp={}local offset=SSSJ[k][1]*4 local num=SSSJ[k][2]for i,v in ipairs(result) do tmp[#tmp+1]={}tmp[#tmp].address=v.address+offset tmp[#tmp].flags=v.flags end tmp=gg.getValues(tmp)for i,v in ipairs(tmp) do if (v.value~=num)then result[i].isUseful=false end end end for i,v in ipairs(result) do if (v.isUseful)then data[#data+1]=v.address end end if data[1]==nil then gg.toast("เปิด")else if NCLX[4]~=false then jldz[NCLX[4]]=data KYXG(data,XGSJ,GNM,"แล้ว")else KYXG(data,XGSJ,GNM,"พบ")end end else gg.toast(GNM.."เปิด☒")end else KYXG(jldz[NCLX[4]],XGSJ,GNM,"เรียกร้องให้")end end
function split(szFullString, szSeparator) local nFindStartIndex = 1 local nSplitIndex = 1 local nSplitArray = {} while true do local nFindLastIndex = string.find(szFullString, szSeparator, nFindStartIndex) if not nFindLastIndex then nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, string.len(szFullString)) break end nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, nFindLastIndex - 1) nFindStartIndex = nFindLastIndex + string.len(szSeparator) nSplitIndex = nSplitIndex + 1 end return nSplitArray end function xgxc(szpy, qmxg) for x = 1, #(qmxg) do xgpy = szpy + qmxg[x]["offset"] xglx = qmxg[x]["type"] xgsz = qmxg[x]["value"] gg.setValues({[1] = {address = xgpy, flags = xglx, value = xgsz}}) xgsl = xgsl + 1 end end function xqmnb(qmnb) gg.clearResults() gg.setRanges(qmnb[1]["memory"]) gg.searchNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "") else gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "") else sl = gg.getResults(999999) sz = gg.getResultCount() xgsl = 0 if sz > 999999 then sz = 999999 end for i = 1, sz do pdsz = true for v = 4, #(qmnb) do if pdsz == true then pysz = {} pysz[1] = {} pysz[1].address = sl[i].address + qmnb[v]["offset"] pysz[1].flags = qmnb[v]["type"] szpy = gg.getValues(pysz) pdpd = qmnb[v]["lv"] .. ";" .. szpy[1].value szpd = split(pdpd, ";") tzszpd = szpd[1] pyszpd = szpd[2] if tzszpd == pyszpd then pdjg = true pdsz = true else pdjg = false pdsz = false end end end if pdjg == true then szpy = sl[i].address xgxc(szpy, qmxg) xgjg = true end end if xgjg == true then gg.toast(qmnb[2]["name"] .. "" .. xgsl .. "") else gg.toast(qmnb[2]["name"] .. "") end end end end
local jldz={}function KYXG(DZ,XGSJ,GNM,JLDZ)local t={}for i=1,#DZ do for k,w in ipairs(XGSJ) do offset=w[1]*4 t[#t+1]={}t[#t].address=DZ[i]+offset t[#t].flags=w[2]t[#t].value=w[3]if(w[4]==true)then local item={}item[#item+1]=t[#t]item[#item].freeze=true gg.addListItems(item)end end end gg.setValues(t)gg.toast(GNM.."")end function KY_ZZ(NCLX,SSSJ,XGSJ,GNM)gg.setVisible(false)if jldz[NCLX[4]]==nil then gg.clearResults()gg.setRanges(NCLX[1])gg.searchNumber(NCLX[2],NCLX[3])local count=gg.getResultCount()local result=gg.getResults(count)gg.clearResults()local data={}if(count>0)then for i,v in ipairs(result) do v.isUseful=true end for k=1,#SSSJ do local tmp={}local offset=SSSJ[k][1]*4 local num=SSSJ[k][2]for i,v in ipairs(result) do tmp[#tmp+1]={}tmp[#tmp].address=v.address+offset tmp[#tmp].flags=v.flags end tmp=gg.getValues(tmp)for i,v in ipairs(tmp) do if (v.value~=num)then result[i].isUseful=false end end end for i,v in ipairs(result) do if (v.isUseful)then data[#data+1]=v.address end end if data[1]==nil then gg.toast("")else if NCLX[4]~=false then jldz[NCLX[4]]=data KYXG(data,XGSJ,GNM,"")else KYXG(data,XGSJ,GNM,"")end end else gg.toast(GNM.."")end else KYXG(jldz[NCLX[4]],XGSJ,GNM,"")end end

local gngb="[ปิด]"
local gnkq="[เปิด]"
local ssxz=gngb
local sxxz=gngb
KG = {
1,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0
}
function TS1()
KG[2] = KG[2]+KG[1]
end

function TS2()
KG[2] = KG[2]-KG[1]
end

function CQ1()
KG[3] = KG[3]+KG[1]
end

function CQ2()
KG[3] = KG[3]-KG[1]
end

function SS1()
KG[4] = KG[4]+KG[1]
end

function SS2()
KG[4] = KG[4]-KG[1]
end

function TX1()
KG[5] = KG[5]+KG[1]
end

function TX2()
KG[5] = KG[5]-KG[1]
end

function YS1()
KG[6] = KG[6]+KG[1]
end

function YS2()
KG[6] = KG[6]-KG[1]
end

function LT1()
KG[7] = KG[7]+KG[1]
end

function LT2()
KG[7] = KG[7]-KG[1]
end

function ZH1()
KG[8] = KG[8]+KG[1]
end

function ZH2()
KG[8] = KG[8]-KG[1]
end

function XZ1()
KG[9] = KG[9]+KG[1]
end

function XZ2()
KG[9] = KG[9]-KG[1]
end

function DD1()
KG[10] = KG[10]+KG[1]
end

function DD2()
KG[10] = KG[10]-KG[1]
end

function FW1()
KG[11] = KG[11]+KG[1]
end

function FW2()
KG[11] = KG[11]-KG[1]
end

function WK1()
KG[12] = KG[12]+KG[1]
end

function WK2()
KG[12] = KG[12]-KG[1]
end

function BJ1()
KG[13] = KG[13]+KG[1]
end

function BJ2()
KG[13] = KG[13]-KG[1]
end

function LTX1()
KG[14] = KG[14]+KG[1]
end

function LTX2()
KG[14] = KG[14]-KG[1]
end

function RWYS1()
KG[15] = KG[15]+KG[1]
end

function RWYS2()
KG[15] = KG[15]-KG[1]
end

function STCQ1()
KG[16] = KG[16]+KG[1]
end

function STCQ2()
KG[16] = KG[16]-KG[1]
end

function QTDG1()
KG[17] = KG[17]+KG[1]
end

function QTDG2()
KG[17] = KG[17]-KG[1]
end

function STLC1()
KG[18] = KG[18]-KG[1]
end

function STLC2()
KG[18] = KG[18]+KG[1]
end

function RWFT1()
KG[19] = KG[19]-KG[1]
end

function RWFT2()
KG[19] = KG[19]+KG[1]
end

function index()
if KG[2] == 0 then
  TS = "□"
else
  TS = "■"
end
if KG[3] == 0 then
  CQ = "□"
else
  CQ = "■"
end
if KG[4] == 0 then
  SS = "□"
else
  SS = "■"
end
if KG[5] == 0 then
  TX = "□"
else
  TX = "■"
end
if KG[6] == 0 then
  YS = "□"
else
  YS = "■"
end
if KG[7] == 0 then
  LT = "□"
else
  LT = "■"
end
if KG[8] == 0 then
  ZH = "□"
else
  ZH = "■"
end
if KG[9] == 0 then
  XZ = "□"
else
  XZ = "■"
end
if KG[10] == 0 then
  DD = "□"
else
  DD = "■"
end
if KG[11] == 0 then
  FW = "□"
else
  FW = "■"
end
if KG[12] == 0 then
  WK = "□"
else
  WK = "■"
end
if KG[13] == 0 then
  BJ = "□"
else
  BJ = "■"
end
if KG[14] == 0 then
  LTX = "□"
else
  LTX = "■"
end
if KG[15] == 0 then
  RWYS = "□"
else
  RWYS = "■"
end
if KG[16] == 0 then
  STCQ = "□"
else
  STCQ = "■"
end
if KG[17] == 0 then
  QTDG = "□"
else
  QTDG = "■"
end
if KG[18] == 0 then
  STLC = "□"
else
  STLC = "■"
end
if KG[19] == 0 then
  RWFT = "□"
else
  RWFT = "■"
end
MF = gg.choice({
  " โหมดต่อสู้ ",
  " มุมมอง ",
  " อาคาร ",
  " ตัวละคร ",
  " แบบพิเศษ ",
  " ขี้เกียจเปิด(เปิดฟังชั่น PVP) ",
  " ปิด "
}, nil, "รุ่นที่ปรับให้เหมาะสม/ขี้เกียจเปิด:ตัวเขียว/ไฮไลต์/เสาอากาศ/เปลี่ยนบ่าย/วินาที/" .. "\nถาวร")
if MF == 1 then
  A()
end
if MF == 2 then
  B()
end
if MF == 3 then
  E()
end
if MF == 4 then
  C()
end
if MF == 5 then
  W()
end
if MF == 6 then
  LR()
end
if MF == 7 then
  exit()
end
XGCK = -1
end

function A()
MF1 = gg.multiChoice({
  " 1. กระสุนวิเศษ1 [ปลอดภัย 90%]",
  " 2. กระสุนวิเศษ2 [ปลอดภัย 100%]",
  " 3. ล็อกแบบดูด",
  " 4. ยิงทะลุ [ใหม่]",
  " 5. ยิงไว",
  " 6. ลูฟี่",
  " 7. สโคป x10 " .. BJ,
  " 8. ล็อกแบบแข็ง ",
  " 9. ปืนไม่ดีด ",
  " 10. เปลี่ยนกระสุนไว ",
  " 11. กลับไปที่รายการ "
}, nil, "การเปิดโดยตรงขนาดใหญ่พิเศษล่าสุดสิ้นสุดลงแล้ว")
if MF1[1] ==true then
  amfw()
end
if MF1[2] ==true then
  mgasddd()
end
if MF1[3] ==true then
  qszm()
end
if MF1[4] ==true then
  adgasd()
end
if MF1[5] ==true then
  qqsb()
end
if MF1[6] ==true then
  A5()
end
if MF1[7] ==true then
  asd8()
end
if MF1[8] ==true then
  qpzm()
end
if MF1[9] ==true then
  whzq()
end
if MF1[10] ==true then
  qqmh()
end
if MF1[11] ==true then
  index()
end
XGCK = -1
end

function B()
MF2 = gg.multiChoice({
  " 1.มองบ้าน",
  " 2.ลบกำแพง " .. TS,
  " 3.เสาบ้าน " .. FW,
  " 4.การแปลงกลางวันและกลางคืน " .. ZH,
  " 5.กลับไปที่รายการ "
}, nil, "")
if MF2[1] ==true then
  B1()
end
if MF2[2] ==true then
  B2()
end
if MF2[3] ==true then
  B3()
end
if MF2[4] ==true then
  B4()
end
if MF2[5] ==true then
  index()
end
XGCK = -1
end

function C()
MF3 = gg.multiChoice({
  " 1.Snapdragon สีขาว ",
  " 2.Snapdragon สีม่วง ",
  " 3.Snapdragon รวมสี ",
  " 4.เสาอากาศพิเศษ [เปิดครั้งเดียว]",
  " 5.มองกลางคืน ",
  " 6.สีเงิน ",
  " 7.ลบหญ่า&ต้นไม้",
  " 8.จมดินครึ่งตัว ",
  " 9.เพิ่มมความเร็ว ",
  " 10.มุมมมองไกล",
  " 11.การเร่งความเร็วทางกายภาพ ",
  " 12.ตัวขาว [New] ",
  " 13.ไฮไลต์ตัว ",
  " 14.มองเสาแร่",
  " 15.มองทะลุ ",
  " 16.เสาอากาศสัญลักษณ์ (ลูป) ",
  " 17.เส้นบางของตัวละคร (ลูป) ",
  " 18.ร่อน ",
  " 19.เดินใต้น้ำ ",
  " 20.มองมุมสูง(นั่ง)",
  " 21.สี Lianfa ",
  " 22.กลับไปที่รายการ "
}, nil, "ฟังก์ชั่นส่วนใหญ่เป็น Snapdragon 500+")
if MF3[1] ==true then
  C1()
end
if MF3[2] ==true then
  C9()
end
if MF3[3] ==true then
  C10()
end
if MF3[4] ==true then
  C2()
end
if MF3[5] ==true then
  C3()
end
if MF3[6] ==true then
  C4()
end
if MF3[7] ==true then
  C5()
end
if MF3[8] ==true then
  C6()
end
if MF3[9] ==true then
  C7()
end
if MF3[10] ==true then
  C8()
end
if MF3[11] ==true then
  stjs()
end
if MF3[12] ==true then
  hs()
end
if MF3[13] ==true then
  wgl()
end
if MF3[14] ==true then
  wztx()
end
if MF3[15] ==true then
  rwts()
end
if MF3[16] ==true then
  D()
end
if MF3[17] ==true then
  drxx()
end
if MF3[18] ==true then
  rwft()
end
if MF3[19] ==true then
  sxxz()
end
if MF3[20] ==true then
  qlss()
end
if MF3[21] ==true then
  lfkss()
end
if MF3[22] ==true then
  index()
end
XGCK = -1
end

function W()
MF1 = gg.multiChoice({
  " 1.ทะลุกำแพง [1] ",
  " 2.ทะลุกำแพง [2] ",
  " 3.ยิงทะลุ ",
  " 4.ฟันไกล(ห้ามเปิด)",
  " 5.บิน",
  " 6.เดินทะลุ",
  " 7.รออัพเดต",
  " 8.รออัพเดต",
  " 9.สาระสำคัญที่ยืดออก ",
  " 10.หายตัว(ยังไม่สมบูรณ์)",
  " 11.ร่างกายของศัตรูเพิ่มขึ้น",
  " 12.นอนลงและเติบโต ",
  " 13.รออัพเดต",
  " 14.ดำดิน",
  " 15.รออัพเดต",
  " 16.รออัพเดต",
  " 17.รออัพเดต",
  " 18.กลับไปที่รายการ "
}, nil, "เปิด ฟันไกล ระวังโดนแบนนะ")
if MF1[1] ==true then
  stcq()
end
if MF1[2] ==true then
  yk()
end
if MF1[3] ==true then
  adgasd()
end
if MF1[4] ==true then
  zdct()
end
if MF1[5] ==true then
  djft()
end
if MF1[6] ==true then
  asdfg()
end
if MF1[7] ==true then
  index()
end
if MF1[8] ==true then
  index()
end
if MF1[9] ==true then
  qtcq1()
end
if MF1[10] ==true then
  shunyi()
end
if MF1[11] ==true then
  stzg()
end
if MF1[12] ==true then
  stlc()
end
if MF1[13] ==true then
  index()
end
if MF1[14] ==true then
  qtdg()
end
if MF1[15] ==true then
  index()
end
if MF1[16] ==true then
  index()
end
if MF1[17] ==true then
  index()
end
if MF1[18] ==true then
  index()
end
XGCK = -1
end

function whzq()
MF1 = gg.multiChoice({
  " 1.QBZ ",
  " 2.M4 ",
  " 3.AK ",
  " 4.Uzi ",
  " 5.พก ",
  " 6.Famas ",
  " 7.กึ่งอัตโนมัติ ",
  " 8.Uzi ",
  " 9.SMG ",
  " 10.ซองเดี๋ยว",
  " 11.ระเบิด",
  " 12.พกกึ่ง",
  " 13.M762",
  " 14.เปิดทั้งหมด ",
  " 15.กลับไปที่รายการ "
}, nil, "รวมทั้งหมดทีละรายการ")
if MF1[1] ==true then
  qbz()
end
if MF1[2] ==true then
  m4()
end
if MF1[3] ==true then
  ak()
end
if MF1[4] ==true then
  sp()
end
if MF1[5] ==true then
  gz()
end
if MF1[6] ==true then
  dp()
end
if MF1[7] ==true then
  bzd()
end
if MF1[8] ==true then
  uzi()
end
if MF1[9] ==true then
  smg()
end
if MF1[10] ==true then
  ptwh()
end
if MF1[11] ==true then
  m762()
end
if MF1[12] ==true then
  lys()
end
if MF1[13] ==true then
  ldwh()
end
if MF1[14] ==true then
  qqwhy()
end
if MF1[5] ==true then
  index()
end
XGCK = -1
end

function LR()
C1()
qszm()
wgl()
rwts()
amtx()
qqmh()
qqwhy()
asd8()
end

function amfw()

    qmnb = {
    {["memory"] = 4},
    {["name"] = " "},
    {["value"] = 0.4300000071525574, ["type"] = 16},
    {["lv"] = 0.10999999940395355, ["offset"] = -4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --1
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (5%)"},
    {["value"] = 0.44999998807907104, ["type"] = 16},
    {["lv"] = 0.03999999910593033, ["offset"] = -4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --2
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (10%)"},
    {["value"] = 0.5600000023841858, ["type"] = 16},
    {["lv"] = 0.03999999910593033, ["offset"] = -4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --3
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (15%)"},
    {["value"] = 0.36000001430511475, ["type"] = 16},
    {["lv"] = 0.03999999910593033, ["offset"] = -4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --4
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (20%)"},
    {["value"] = 0.2750000059604645, ["type"] = 16},
    {["lv"] = 0.03999999910593033, ["offset"] = -4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --5
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (25%)"},
    {["value"] = 0.1899999976158142, ["type"] = 16},
    {["lv"] = 0.10999999940395355, ["offset"] = -4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --6
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (30%)"},
    {["value"] = 0.23999999463558197, ["type"] = 16},
    {["lv"] = 0.10999999940395355, ["offset"] = -4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --7
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (35%)"},
    {["value"] = 0.33000001311302185, ["type"] = 16},
    {["lv"] = 0.10999999940395355, ["offset"] = -4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --8
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (40%)"},
    {["value"] = 0.5400000214576721, ["type"] = 16},
    {["lv"] = 0.09000000357627869, ["offset"] = -4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --9
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (45%)"},
    {["value"] = 0.6899999976158142, ["type"] = 16},
    {["lv"] = 0.1599999964237213, ["offset"] = -4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --10
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (50%)"},
    {["value"] = 0.5099999904632568, ["type"] = 16},
    {["lv"] = 0.03999999910593033, ["offset"] = 4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --11
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (55%)"},
    {["value"] = 0.4300000071525574, ["type"] = 16},
    {["lv"] = 0.05999999865889549, ["offset"] = -4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --12
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (60%)"},
    {["value"] = 0.4417000114917755, ["type"] = 16},
    {["lv"] = 0.05999999865889549, ["offset"] = 4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --13
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (65%)"},
    {["value"] = 0.3100000023841858, ["type"] = 16},
    {["lv"] = 0.09000000357627869, ["offset"] = 4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --14
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (70%)"},
    {["value"] = 0.6800000071525574, ["type"] = 16},
    {["lv"] = 0.10999999940395355, ["offset"] = 4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --15
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (75%)"},
    {["value"] = 0.5000153183937073, ["type"] = 16},
    {["lv"] = 0.10999999940395355, ["offset"] = 4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --16
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (80%)"},
    {["value"] = 0.30000001192092896, ["type"] = 16},
    {["lv"] = 0.10999999940395355, ["offset"] = 4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --17
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (85%)"},
    {["value"] = 0.23800000548362732, ["type"] = 16},
    {["lv"] = 0.10999999940395355, ["offset"] = 4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --18
    qmnb = {
    {["memory"] = 4},
    {["name"] = " ทำงาน (96%)"},
    {["value"] = 0.30000001192092896, ["type"] = 16},
    {["lv"] = 0.699999988079071, ["offset"] = -4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    --19
    qmnb = {
    {["memory"] = 4},
    {["name"] = "ทำงาน (100%)"},
    {["value"] = 0.7071068286895752, ["type"] = 16},
    {["lv"] = 0.009999999776482582, ["offset"] = 4, ["type"] = 16},
    }
    qmxg = {
    {["value"] = 99, ["offset"] = 0, ["type"] = 16},
    
    }
    xqmnb(qmnb)
    amfw()
    end
    
function mgasddd() -- กระสุนติดตาม
SearchWrite({
  {
  "0.09000000357627869",
  0
  },
  {
  "3.60133705331478E-43",
  -4
  }
}, {
  {
  50,
  4,
  false
  }
}, gg.REGION_C_BSS, "")
SearchWrite({
  {
  "0.1599999964237213",
  0
  },
  {
  "3.60133705331478E-43",
  -4
  }
}, {
  {
  50,
  4,
  false
  }
}, gg.REGION_C_BSS, "")
SearchWrite({
  {
  "0.10999999940395355",
  0
  },
  {
  "3.60133705331478E-43",
  -4
  }
}, {
  {
  50,
  4,
  false
  }
}, gg.REGION_C_BSS, "")
SearchWrite({
  {
  "0.05999999865889549",
  0
  },
  {
  "3.60133705331478E-43",
  -4
  }
}, {
  {
  50,
  4,
  false
  }
}, gg.REGION_C_BSS, "")
SearchWrite({
  {
  "0.03999999910593033",
  0
  },
  {
  "3.60133705331478E-43",
  -4
  }
}, {
  {
  50,
  4,
  false
  }
}, gg.REGION_C_BSS, "")
mgasddd()
end

function stlc()
if KG[18] == 0 then
  qmnb = {
  {memory = 4},
  {
      name = "นอนลงและเติบโต"
  },
  {
      value = "0.5213000178337097",
      type = 16
  },
  {
      lv = "0.02710000053048134",
      offset = -504,
      type = 16
  }
  }
  qmxg = {
  {
      value = -2.0271000005304813,
      offset = -504,
      type = 16
  }
  }
  xqmnb(qmnb)
  qmnb = {
  {memory = 4},
  {
      name = "หมอบลง"
  },
  {
      value = "0.7275999784469604",
      type = 16
  },
  {
      lv = "-0.020899999886751175",
      offset = -608,
      type = 16
  }
  }
  qmxg = {
  {
      value = -2.1208999998867513,
      offset = -608,
      type = 16
  }
  }
  xqmnb(qmnb)
  qmnb = {
  {memory = 4},
  {
      name = "ยืดตรง"
  },
  {
      value = "0.4503999948501587",
      type = 16
  },
  {
      lv = "-0.020800000056624413",
      offset = -604,
      type = 16
  }
  }
  qmxg = {
  {
      value = -2.1208000000566245,
      offset = -604,
      type = 16
  }
  }
  xqmnb(qmnb)
  STLC1()
else
  qmnb = {
  {memory = 4},
  {
      name = "นอนลงและเติบโต"
  },
  {
      value = "0.5213000178337097",
      type = 16
  },
  {
      lv = "-2.02710000053048134",
      offset = -504,
      type = 16
  }
  }
  qmxg = {
  {
      value = 0.02710000053048134,
      offset = -504,
      type = 16
  }
  }
  xqmnb(qmnb)
  qmnb = {
  {memory = 4},
  {
      name = "หมอบลง"
  },
  {
      value = "0.7275999784469604",
      type = 16
  },
  {
      lv = "-2.120899999886751175",
      offset = -608,
      type = 16
  }
  }
  qmxg = {
  {
      value = -0.020899999886751175,
      offset = -608,
      type = 16
  }
  }
  xqmnb(qmnb)
  qmnb = {
  {memory = 4},
  {
      name = "ยืดตรง"
  },
  {
      value = "0.4503999948501587",
      type = 16
  },
  {
      lv = "-2.120800000056624413",
      offset = -604,
      type = 16
  }
  }
  qmxg = {
  {
      value = -0.020800000056624413,
      offset = -604,
      type = 16
  }
  }
  xqmnb(qmnb)
  STLC2()
end
end

function qqwhy()
qbz()
m4()
ak()
sp()
gz()
dp()
bzd()
uzi()
smg()
ptwh()
ldwh()
m762()
lys()
end

function sxxz()
F = gg.alert("เดินใต้น้ำ", "เปิด", "ปิด")
if F == 1 then
  qmnb = {
  {memory = 4},
  {name = "ความสำเร็จ"},
  {
      value = "10000.001953125",
      type = 16
  },
  {
      lv = "10000.0",
      offset = -4,
      type = 16
  }
  }
  qmxg = {
  {
      value = 0,
      offset = -4,
      type = 16
  }
  }
  xqmnb(qmnb)
elseif F == 2 then
  qmnb = {
  {memory = 4},
  {name = "ปิด"},
  {
      value = "10000.001953125",
      type = 16
  },
  {
      lv = "0",
      offset = -4,
      type = 16
  }
  }
  qmxg = {
  {
      value = 10000,
      offset = -4,
      type = 16
  }
  }
  xqmnb(qmnb)
end
end

function qtcq1()
F = gg.alert("เกมที่สวมใส่ได้สร้างอาคารที่ไม่ใช่ผู้เล่น，ห้องบัตรไม่ทำงาน，คุณสามารถหาอาคารเพื่อเข้าไปและเอาชนะผู้คนได้", "เปิดผ่านผนัง", "ปิด")
if F == 1 then
  qtcq()
elseif F == 2 then
  qtcqg()
end
end

function ld()
F = gg.alert("เคล็ดลับ 1:หากการเปิดไม่ถูกต้องโปรดรีสตาร์ท", "ถนนกิเมียวดัน", "เปิด", "ปิดโล่ถนน")
if F == 1 then
  gg.clearResults()
  KY_ZZ({
  "32",
  "1036831949",
  "4",
  false
  }, {
  {"-10", "1082088489"}
  }, {
  {
      "17",
      "16",
      "-1.8"
  }
  }, "ความสำเร็จ")
  gg.clearList()
elseif F == 2 then
  gg.clearResults()
  KY_ZZ({
  "32",
  "1036831949",
  "4",
  false
  }, {
  {"-10", "1082088489"}
  }, {
  {
      "15",
      "16",
      "1.8"
  }
  }, "ความสำเร็จ")
  gg.clearList()
elseif F == 3 then
  gg.clearResults()
  KY_ZZ({
  "32",
  "1036831949",
  "4",
  false
  }, {
  {"-10", "1082088489"}
  }, {
  {
      "17",
      "16",
      "0"
  }
  }, "ความสำเร็จ")
  gg.clearList()
  gg.clearResults()
  KY_ZZ({
  "32",
  "1036831949",
  "4",
  false
  }, {
  {"-10", "1082088489"}
  }, {
  {
      "15",
      "16",
      "0"
  }
  }, "ความสำเร็จ")
  gg.clearList()
end
end

function shunyi()
  gg.clearList()
gg.clearResults()
gg.searchNumber('"1.2611686e-44;2.3509887e-38;2.0:13"', gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.refineNumber('"2"', gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(99999)
gg.editAll('"130"', gg.TYPE_FLOAT)
gg.clearList()
gg.toast("หายตัว")
gg.clearResults()

end

function qtcq()
qmnb = {
  {memory = 4},
  {name = "ทะลุกำแพง"},
  {
  value = "0.38333338499069214",
  type = 16
  },
  {
  lv = "1.0000000331813535E32",
  offset = -16,
  type = 16
  },
  {
  lv = "0.0024999999441206455",
  offset = -8,
  type = 16
  }
}
qmxg = {
  {
  value = 9,
  offset = -16,
  type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 32},
  {name = "ทะลุกำแพง"},
  {
  value = "6.699999809265137",
  type = 16
  },
  {
  lv = "0.10000000149011612",
  offset = 16,
  type = 16
  }
}
qmxg = {
  {
  value = -999,
  offset = 16,
  type = 16
  }
}
xqmnb(qmnb)
end

function qtcqg()
qmnb = {
  {memory = 4},
  {name = "ปิดทะลุกำแพง"},
  {value = 0.10000000149011612, type = 16},
  {
  lv = 9,
  offset = 4,
  type = 16
  },
  {
  lv = 0.004999999888241291,
  offset = 8,
  type = 16
  }
}
qmxg = {
  {
  value = 1.0000000331813535E32,
  offset = 4,
  type = 16
  }
}
xqmnb(qmnb)
end

function hs()
  gg.setRanges(gg.REGION_C_ALLOC)
  gg.searchNumber("0.75;0.0;3.5873241e-43:49", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.refineNumber("0.75", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  revert = gg.getResults(1000, nil)
  gg.editAll("999", gg.TYPE_FLOAT)
  gg.clearResults()
  gg.toast("ตัวขาว👻")
  
  end

function wztx()
qmnb = {
  {memory = 1048576},
  {name = "เสาอากาศกัญชา"},
  {
  value = "0.28343823552131653",
  type = 16
  },
  {
  lv = "1.0718156099319458",
  offset = 4,
  type = 16
  }
}
qmxg = {
  {
  value = 999,
  offset = 4,
  type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 1048576},
  {
  name = "เสาอากาศกำมะถัน"
  },
  {
  value = "0.2962999939918518",
  type = 16
  },
  {
  lv = "0.06840000301599503",
  offset = 4,
  type = 16
  }
}
qmxg = {
  {
  value = 999,
  offset = 4,
  type = 16
  }
}
xqmnb(qmnb)
end

function wgl()
qmnb = {
  {memory = 1048576},
  {name = "ไฮไลต์"},
  {
  value = "0.040008544921875",
  type = 16
  },
  {
  lv = "0.9599609375",
  offset = -8,
  type = 16
  }
}
qmxg = {
  {
  value = 120,
  offset = -8,
  type = 16
  }
}
xqmnb(qmnb)
end

function rwts()
  gg.clearResults()
  gg.setRanges(gg.REGION_VIDEO)
  gg.searchNumber("5.127597087642792E-29", 16)
  gg.getResults(9)
  gg.editAll("5.127597087642792E29", 16)
  gg.toast("เปิด" .. gg.getResultCount() .. " เปลี่ยนแปลง")
  gg.clearResults()
end

function pxdd()
F = gg.alert("ให้ความสนใจ/ถ้าเปิดความสำเร็จหากคุณตายบนพื้นโปรดใช้ซอฟต์แวร์แก้ไขเพื่อแก้ไข (ดาวน์โหลดจากดิสก์เครือข่าย)", "เปิด", "ปิด")
if F == 1 then
  qw()
elseif F == 2 then
  qe()
end
end

function dxdd()
qmnb = {
  {memory = 4},
  {
  name = "หมอบลง"
  },
  {
  value = "0.7300000190734863",
  type = 16
  },
  {
  lv = "1.401298464324817E-45",
  offset = -8,
  type = 16
  }
}
qmxg = {
  {
  value = 2,
  offset = 0,
  type = 16,
  freeze = true
  }
}
xqmnb(qmnb)
end

function qw()
qmnb = {
  {memory = 4},
  {
  name = "โพรบลง"
  },
  {
  value = "-0.093299999833107",
  type = 16
  },
  {
  lv = "0.02710000053048134",
  offset = -8,
  type = 16
  }
}
qmxg = {
  {
  value = -1.1298777777777,
  offset = -8,
  type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {name = "โล่เต็ม"},
  {
  value = "0.41999998688697815",
  type = 16
  },
  {
  lv = "2.802596928649634E-45",
  offset = 8,
  type = 16
  },
  {
  lv = "0.41999998688697815",
  offset = 16,
  type = 16
  }
}
qmxg = {
  {
  value = 1.14987659454,
  offset = 16,
  type = 16,
  freeze = true
  }
}
xqmnb(qmnb)
end

function stzg()
qmnb = {
  {memory = 4},
  {
  name = "ร่างกายของศัตรูเพิ่มขึ้น"
  },
  {
  value = "0.10490000247955322",
  type = 16
  },
  {
  lv = "-0.3138999938964844",
  offset = 148,
  type = 16
  }
}
qmxg = {
  {
  value = -1.3138999938964844,
  offset = 148,
  type = 16
  }
}
xqmnb(qmnb)
end

function dxjj()
qmnb = {
  {memory = 16384},
  {name = "ใต้ดิน"},
  {value = "2.0", type = 16},
  {
  lv = "-2.0",
  offset = 4,
  type = 16
  },
  {
  lv = "2.0",
  offset = 8,
  type = 16
  },
  {
  lv = "0.0",
  offset = 12,
  type = 16
  },
  {
  lv = "1.0",
  offset = 24,
  type = 16
  },
  {
  lv = "1.0",
  offset = 36,
  type = 16
  },
  {
  lv = "1.0",
  offset = 48,
  type = 16
  }
}
qmxg = {
  {
  value = 1.87,
  offset = 0,
  type = 16
  },
  {
  value = 1.87,
  offset = 8,
  type = 16
  }
}
xqmnb(qmnb)
end

function stjs()
qmnb = {
  {memory = 16384},
  {name = "เร่งความเร็ว"},
  {
  value = "-9.187806369957434E35",
  type = 16
  },
  {
  lv = "-0.5035263299942017",
  offset = 4,
  type = 16
  },
  {
  lv = "-0.5029144287109375",
  offset = 8,
  type = 16
  },
  {
  lv = "-3.1514847038785864E24",
  offset = 12,
  type = 16
  },
  {
  lv = "0.14177720248699188",
  offset = 16,
  type = 16
  },
  {
  lv = "8.725451134826695E-39",
  offset = 28,
  type = 16
  },
  {
  lv = "8.724907431022537E-39",
  offset = 32,
  type = 16
  },
  {
  lv = "8.724784116757677E-39",
  offset = 36,
  type = 16
  },
  {
  lv = "8.724865392068607E-39",
  offset = 40,
  type = 16
  }
}
qmxg = {
  {
  value = 0.14577720248699189,
  offset = 0,
  type = 16
  },
  {
  value = 0.14577720248699189,
  offset = 16,
  type = 16
  }
}
xqmnb(qmnb)
end

function rwft()
  gg.setRanges(gg.REGION_CODE_APP)
  gg.searchNumber('0.60000002384F;0.73000001907F',gg.TYPE_FLOAT,false ,gg.SIGN_EQUAL,0,-1)
  gg.searchNumber('0.60000002384',gg.TYPE_FLOAT,false,gg.SIGN_EQUAL,0,-1)
  gg.getResults(100)
  gg.editAll('999',gg.TYPE_FLOAT)
  end

function ft()
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("16,256W;1.03~1.042F;16,261W;-26,214W;15,897W::", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("1.03~1.042", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
jg = gg.getResults(100)
sl = gg.getResultCount()
if 100 < sl then
  sl = 100
end
for _FORV_3_ = 1, sl do
  dzy = jg[_FORV_3_].address
  gg.addListItems({
  [1] = {
      address = dzy,
      flags = gg.TYPE_FLOAT,
      freeze = true,
      value = 0.37698
  }
  })
end
end

function ddlf()
qmnb = {
  {memory = 16384},
  {
  name = "ตายแค่ครั้งเดียว"
  },
  {value = "2.0", type = 16},
  {
  lv = "-2.0",
  offset = 4,
  type = 16
  },
  {
  lv = "2.0",
  offset = 8,
  type = 16
  },
  {
  lv = "0.0",
  offset = 12,
  type = 16
  },
  {
  lv = "1.0",
  offset = 24,
  type = 16
  },
  {
  lv = "1.0",
  offset = 36,
  type = 16
  },
  {
  lv = "1.0",
  offset = 48,
  type = 16
  }
}
qmxg = {
  {
  value = 1.98,
  offset = 0,
  type = 16
  },
  {
  value = 1.98,
  offset = 8,
  type = 16
  }
}
xqmnb(qmnb)
gg.setRanges(36)
gg.searchNumber("0.09059999883;-0.31400001049F;0.02710000053", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("0.02710000053", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(90000)
gg.editAll("-1.1298777777777", gg.TYPE_FLOAT)
gg.clearResults()
end

function D()
gg.clearResults()
if gg.isVisible() == true then
else
  qmnb = {
  {memory = 4},
  {name = "ประสานงาน"},
  {
      value = "0.16947640478610992",
      type = 16
  },
  {
      lv = "-0.9855342507362366",
      offset = 4,
      type = 16
  },
  {
      lv = "-0.9855342507362366",
      offset = 16,
      type = 16
  }
  }
  qmxg = {
  {
      value = -999,
      offset = 4,
      type = 16
  },
  {
      value = -999,
      offset = 16,
      type = 16
  }
  }
  xqmnb(qmnb)
  if gg.isVisible() == true then
  else
  D()
  end
end
end

function amtx()
qmnb = {
  {memory = 4},
  {name = "ประสานงาน"},
  {
  value = "0.16947640478610992",
  type = 16
  },
  {
  lv = "-0.9855342507362366",
  offset = 4,
  type = 16
  },
  {
  lv = "-0.9855342507362366",
  offset = 16,
  type = 16
  }
}
qmxg = {
  {
  value = -999,
  offset = 4,
  type = 16
  },
  {
  value = -999,
  offset = 16,
  type = 16
  }
}
xqmnb(qmnb)
end

function E()
MF5 = gg.multiChoice({
  " ใต้ดินลึก ",
  " สร้างบ้านใต้ดิน ",
  " ผ่านเพดาน ",
  " กลับไปที่รายการ "
}, nil, "ผ่านเพดานวิธีการใช้คือในช่องว่างระหว่างเพดานทั้งสองเปิดแล้วลงและออฟไลน์เป็นเวลาเจ็ดนาทีและออนไลน์ได้")
if MF5[1] ==true then
  E1()
end
if MF5[2] ==true then
  E2()
end
if MF5[3] ==true then
  E3()
end
if MF5[4] ==true then
  index()
end
XGCK = -1
end

function A1()
  SearchWrite({{"0.09000000357627869",0},{"3.60133705331478E-43",-4}}, {{50,4,false}}, gg.REGION_C_BSS, "")
  SearchWrite({{"0.1599999964237213",0},{"3.60133705331478E-43",-4}}, {{50,4,false}}, gg.REGION_C_BSS, "")
  SearchWrite({{"0.10999999940395355",0},{"3.60133705331478E-43",-4}}, {{50,4,false}}, gg.REGION_C_BSS, "")
  SearchWrite({{"0.05999999865889549",0},{"3.60133705331478E-43",-4}}, {{50,4,false}}, gg.REGION_C_BSS, "")
  SearchWrite({{"0.03999999910593033",0},{"3.60133705331478E-43",-4}}, {{50,4,false}}, gg.REGION_C_BSS, "กระสุนติดตาม")
A1(string.rep(99, 450000))
  SearchWrite({{"0.09000000357627869",0},{"3.60133705331478E-43",-4}}, {{50,4,false}}, gg.REGION_C_BSS, "")
  SearchWrite({{"0.1599999964237213",0},{"3.60133705331478E-43",-4}}, {{50,4,false}}, gg.REGION_C_BSS, "")
  SearchWrite({{"0.10999999940395355",0},{"3.60133705331478E-43",-4}}, {{50,4,false}}, gg.REGION_C_BSS, "")
  SearchWrite({{"0.05999999865889549",0},{"3.60133705331478E-43",-4}}, {{50,4,false}}, gg.REGION_C_BSS, "")
  SearchWrite({{"0.03999999910593033",0},{"3.60133705331478E-43",-4}}, {{50,4,false}}, gg.REGION_C_BSS, "กระสุนติดตาม")
  -- กระสุนวิเศษ
end

function qszm()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("2.0F;0.20000000298F;1.20000004768F;1.5F;1.0F;0.10000000149F:512", gg.TYPE_FLOAT,false,gg.SIGN_EQUAL,0, -1)
gg.searchNumber("2.0", gg.TYPE_FLOAT,false,gg.SIGN_EQUAL,0,-1)
gg.getResults(1)
gg.editAll("2.0",gg.TYPE_FLOAT)
gg.toast("เปิด")
end

function qpzm()
qmnb = {
  {memory = 16384},
  {
  name = "การมองเห็นแบบเต็มหน้าจอ"
  },
  {
  value = "-6.171913993364983E27",
  type = 16
  },
  {
  lv = "-1.0061304023208683E28",
  offset = 4,
  type = 16
  },
  {
  lv = "-1.220370790326068E21",
  offset = 8,
  type = 16
  }
}
qmxg = {
  {
  value = 10,
  offset = 4,
  type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 16384},
  {name = "เล็งด้วยตนเอง"},
  {
  value = -"5.475527268489559E27",
  type = 16
  },
  {
  lv = "-3.693674733290232E20",
  offset = -8,
  type = 16
  },
  {
  lv = "-8.345310621825903E22",
  offset = -4,
  type = 16
  }
}
qmxg = {
  {
  value = 10,
  offset = 0,
  type = 16
  }
}
xqmnb(qmnb)
end

function qqsb()
gg.clearResults()
gg.setRanges(16384)
gg.searchNumber("167,772,163;436,207,616;981,668,463;-509,591,552;-527,499,264;-439,353,344;-442,564,476::", 4, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("981,668,463", 4, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(99)
gg.editAll("940000000", 4)
gg.clearResults()
end

function A5()
F = gg.alert("เทคโนโลยี", "คิเมียวลูฟี่", "ลูฟี่", "ทั้งหมดปิด")
if F == 1 then
  gg.clearResults()
  KY_ZZ({
  "32",
  "1036831949",
  "4",
  false
  }, {
  {"-10", "1082088489"}
  }, {
  {
      "17",
      "16",
      "1.8"
  }
  }, "ลูฟี่")
  gg.clearList()
elseif F == 2 then
  gg.clearResults()
  KY_ZZ({
  "32",
  "1036831949",
  "4",
  false
  }, {
  {"-10", "1082088489"}
  }, {
  {
      "15",
      "16",
      "-1.8"
  }
  }, "ลูฟี่กับสโคป")
  gg.clearList()
elseif F == 3 then
  gg.clearResults()
  KY_ZZ({
  "32",
  "1036831949",
  "4",
  false
  }, {
  {"-10", "1082088489"}
  }, {
  {
      "17",
      "16",
      "0"
  }
  }, "ลูฟี่")
  gg.clearList()
  gg.clearResults()
  KY_ZZ({
  "32",
  "1036831949",
  "4",
  false
  }, {
  {"-10", "1082088489"}
  }, {
  {
      "15",
      "16",
      "0"
  }
  }, "ลูฟี่กับสโคป")
  gg.clearList()
end
end

function qqmh()
qmnb = {
  {memory = 4},
  {
  name = "ชาร์จการเปลี่ยนแปลงครั้งที่สอง"
  },
  {
  value = "0.8845000267028809",
  type = 16
  },
  {
  lv = "1.210721873176642E-42",
  offset = 156,
  type = 16
  },
  {
  lv = "2.0",
  offset = 164,
  type = 16
  }
}
qmxg = {
  {
  value = 0.001,
  offset = 164,
  type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
  name = "อาวุธปืนเป็นเวลา 1 วินาที"
  },
  {
  value = "2.1666667461395264",
  type = 16
  },
  {
  lv = "1.210721873176642E-42",
  offset = -8,
  type = 16
  }
}
qmxg = {
  {
  value = 1.0E-4,
  offset = 0,
  type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
  name = "อาวุธปืนเปลี่ยนครั้งที่สอง 2"
  },
  {
  value = "2.6666667461395264",
  type = 16
  },
  {
  lv = "1.210721873176642E-42",
  offset = -8,
  type = 16
  }
}
qmxg = {
  {
  value = 1.0E-4,
  offset = 0,
  type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
  name = "แก้ไขการเปลี่ยนแปลงที่สอง"
  },
  {
  value = "2.766666889190674",
  type = 16
  },
  {
  lv = "1.210721873176642E-42",
  offset = -8,
  type = 16
  }
}
qmxg = {
  {
  value = 1.0E-4,
  offset = 0,
  type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
  name = "อาวุธปืนเปลี่ยนครั้งที่สอง 3"
  },
  {
  value = "2.0333335399627686",
  type = 16
  },
  {
  lv = "1.210721873176642E-42",
  offset = -8,
  type = 16
  }
}
qmxg = {
  {
  value = 1.0E-4,
  offset = 0,
  type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
  name = "อาวุธปืนเปลี่ยนครั้งที่สอง 4"
  },
  {
  value = "2.90000009537",
  type = 16
  },
  {
  lv = "1.210721873176642E-42",
  offset = -8,
  type = 16
  }
}
qmxg = {
  {
  value = 1.0E-4,
  offset = 0,
  type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
  name = "อาวุธปืนเปลี่ยนครั้งที่สอง5"
  },
  {
  value = "2.83333349228",
  type = 16
  },
  {
  lv = "1.210721873176642E-42",
  offset = -8,
  type = 16
  }
}
qmxg = {
  {
  value = 1.0E-4,
  offset = 0,
  type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
  name = "อาวุธปืนเปลี่ยนครั้งที่สอง6"
  },
  {
  value = "3.500000238418579",
  type = 16
  },
  {
  lv = "1.210721873176642E-42",
  offset = -8,
  type = 16
  }
}
qmxg = {
  {
  value = 0.001,
  offset = 0,
  type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
  name = "อาวุธปืนเปลี่ยนครั้งที่สอง7"
  },
  {
  value = "4.100000381469727",
  type = 16
  },
  {
  lv = "1.210721873176642E-42",
  offset = -8,
  type = 16
  }
}
qmxg = {
  {
  value = 1.0E-4,
  offset = 0,
  type = 16
  }
}
xqmnb(qmnb)
end

function asd8()
  gg.clearList()
  gg.setRanges(32)
  
  SearchWrite({{1111490560, 6584},{0, 6588},{0, 6596}}, {{1084410514,6584,false}}, 4)
  
  gg.clearResults()
  
  gg.setRanges(32)
  
  SearchWrite({{1110704128, 36264},{0, 36256},{0, 36268}}, {{1084410514,36264,false}}, 4)
  
  gg.clearResults()
  
  gg.toast(" Scope X10 ")
  
  end

function lys()
qmnb = {
  {memory = 32},
  {name = "หลุยส์"},
  {value = "480.0", type = 16},
  {
  lv = "20.0",
  offset = -148,
  type = 16
  },
  {
  lv = "40.0",
  offset = -144,
  type = 16
  },
  {
  lv = "6.0",
  offset = -136,
  type = 16
  },
  {
  lv = "60.0",
  offset = -120,
  type = 16
  },
  {
  lv = "0.5",
  offset = -100,
  type = 16
  },
  {
  lv = "4.0",
  offset = 16,
  type = 16
  },
  {
  lv = "4.0",
  offset = 24,
  type = 16
  },
  {
  lv = "1.0",
  offset = 160,
  type = 16
  }
}
qmxg = {
  {
  value = 0,
  offset = -148,
  type = 16
  },
  {
  value = 0,
  offset = -144,
  type = 16
  },
  {
  value = 0,
  offset = -136,
  type = 16
  },
  {
  value = 0,
  offset = -120,
  type = 16
  },
  {
  value = 0,
  offset = -100,
  type = 16
  },
  {
  value = 9999,
  offset = 0,
  type = 16
  },
  {
  value = 0,
  offset = 16,
  type = 16
  },
  {
  value = 0,
  offset = 24,
  type = 16
  },
  {
  value = 0,
  offset = 160,
  type = 16
  }
}
xqmnb(qmnb)
end

function m762()
qmnb = {
  {memory = 32},
  {name = "m762"},
  {value = "735.0", type = 16},
  {
  lv = "15.0",
  offset = -148,
  type = 16
  },
  {
  lv = "33.0",
  offset = -144,
  type = 16
  },
  {
  lv = "6.0",
  offset = -136,
  type = 16
  },
  {
  lv = "20.0",
  offset = -108,
  type = 16
  },
  {
  lv = "10.0",
  offset = -96,
  type = 16
  },
  {
  lv = "10.0",
  offset = -92,
  type = 16
  },
  {
  lv = "10.0",
  offset = -88,
  type = 16
  },
  {
  lv = "4.0",
  offset = 16,
  type = 16
  },
  {
  lv = "4.0",
  offset = 24,
  type = 16
  },
  {
  lv = "1.0",
  offset = 160,
  type = 16
  }
}
qmxg = {
  {
  value = 0,
  offset = -148,
  type = 16
  },
  {
  value = 0,
  offset = -144,
  type = 16
  },
  {
  value = 0,
  offset = -136,
  type = 16
  },
  {
  value = 0,
  offset = -108,
  type = 16
  },
  {
  value = 0,
  offset = -96,
  type = 16
  },
  {
  value = 0,
  offset = -92,
  type = 16
  },
  {
  value = 0,
  offset = -88,
  type = 16
  },
  {
  value = 9999,
  offset = 0,
  type = 16
  },
  {
  value = 0,
  offset = 16,
  type = 16
  },
  {
  value = 0,
  offset = 24,
  type = 16
  },
  {
  value = 0,
  offset = 160,
  type = 16
  }
}
xqmnb(qmnb)
end

function qbz()
qmnb = {
  {memory = 32},
  {name = "qbz"},
  {value = "12.0", type = 16},
  {
  lv = "6.0",
  offset = 12,
  type = 16
  },
  {
  lv = "35.0",
  offset = 28,
  type = 16
  },
  {
  lv = "790.0",
  offset = 148,
  type = 16
  },
  {
  lv = "4.0",
  offset = 164,
  type = 16
  },
  {
  lv = "4.0",
  offset = 172,
  type = 16
  },
  {
  lv = "8.0",
  offset = 192,
  type = 16
  }
}
qmxg = {
  {
  value = 0,
  offset = 0,
  type = 16
  },
  {
  value = 0,
  offset = 12,
  type = 16
  },
  {
  value = 0,
  offset = 28,
  type = 16
  },
  {
  value = 99999,
  offset = 148,
  type = 16
  },
  {
  value = 0,
  offset = 164,
  type = 16
  },
  {
  value = 0,
  offset = 172,
  type = 16
  },
  {
  value = 0,
  offset = 192,
  type = 16
  }
}
xqmnb(qmnb)
end

function m4()
qmnb = {
  {memory = 32},
  {name = "m4"},
  {value = 12, type = 16},
  {
  lv = "6.0",
  offset = 12,
  type = 16
  },
  {
  lv = "35.0",
  offset = 28,
  type = 16
  },
  {
  lv = "830.0",
  offset = 148,
  type = 16
  },
  {
  lv = "4.0",
  offset = 164,
  type = 16
  },
  {
  lv = "4.0",
  offset = 172,
  type = 16
  },
  {
  lv = "8.0",
  offset = 192,
  type = 16
  }
}
qmxg = {
  {
  value = 0,
  offset = 0,
  type = 16
  },
  {
  value = 0,
  offset = 12,
  type = 16
  },
  {
  value = 0,
  offset = 28,
  type = 16
  },
  {
  value = 99999,
  offset = 148,
  type = 16
  },
  {
  value = 0,
  offset = 164,
  type = 16
  },
  {
  value = 0,
  offset = 172,
  type = 16
  },
  {
  value = 0,
  offset = 192,
  type = 16
  }
}
xqmnb(qmnb)
end

function ak()
qmnb = {
  {memory = 32},
  {name = "ak"},
  {value = 14, type = 16},
  {
  lv = "6.0",
  offset = 12,
  type = 16
  },
  {
  lv = "40.0",
  offset = 28,
  type = 16
  },
  {
  lv = "735.0",
  offset = 148,
  type = 16
  },
  {
  lv = "4.0",
  offset = 164,
  type = 16
  },
  {
  lv = "4.0",
  offset = 172,
  type = 16
  },
  {
  lv = "8.0",
  offset = 192,
  type = 16
  }
}
qmxg = {
  {
  value = 0,
  offset = 0,
  type = 16
  },
  {
  value = 0,
  offset = 12,
  type = 16
  },
  {
  value = 0,
  offset = 28,
  type = 16
  },
  {
  value = 99999,
  offset = 148,
  type = 16
  },
  {
  value = 0,
  offset = 164,
  type = 16
  },
  {
  value = 0,
  offset = 172,
  type = 16
  },
  {
  value = 0,
  offset = 192,
  type = 16
  }
}
xqmnb(qmnb)
end

function sp()
qmnb = {
  {memory = 32},
  {
  name = "Uzi"
  },
  {value = 45, type = 16},
  {
  lv = "3.0",
  offset = 12,
  type = 16
  },
  {
  lv = "60.0",
  offset = 28,
  type = 16
  },
  {
  lv = "300.0",
  offset = 148,
  type = 16
  },
  {
  lv = "15.0",
  offset = 164,
  type = 16
  },
  {
  lv = "8.0",
  offset = 192,
  type = 16
  }
}
qmxg = {
  {
  value = 0,
  offset = 0,
  type = 16
  },
  {
  value = 0,
  offset = 12,
  type = 16
  },
  {
  value = 0,
  offset = 28,
  type = 16
  },
  {
  value = 99999,
  offset = 148,
  type = 16
  },
  {
  value = 0,
  offset = 164,
  type = 16
  },
  {
  value = 0,
  offset = 192,
  type = 16
  }
}
xqmnb(qmnb)
end

function gz()
qmnb = {
  {memory = 32},
  {
  name = "พก"
  },
  {value = 14, type = 16},
  {
  lv = "3.0",
  offset = 12,
  type = 16
  },
  {
  lv = "25.0",
  offset = 28,
  type = 16
  },
  {
  lv = "360.0",
  offset = 148,
  type = 16
  },
  {
  lv = "4.0",
  offset = 164,
  type = 16
  },
  {
  lv = "4.0",
  offset = 172,
  type = 16
  },
  {
  lv = "5.0",
  offset = 192,
  type = 16
  }
}
qmxg = {
  {
  value = 0,
  offset = 0,
  type = 16
  },
  {
  value = 0,
  offset = 12,
  type = 16
  },
  {
  value = 0,
  offset = 28,
  type = 16
  },
  {
  value = 99999,
  offset = 148,
  type = 16
  },
  {
  value = 0,
  offset = 164,
  type = 16
  },
  {
  value = 0,
  offset = 172,
  type = 16
  },
  {
  value = 0,
  offset = 192,
  type = 16
  }
}
xqmnb(qmnb)
end

function dp()
qmnb = {
  {memory = 32},
  {
  name = "famas"
  },
  {value = 45, type = 16},
  {
  lv = "3.0",
  offset = 12,
  type = 16
  },
  {
  lv = "60.0",
  offset = 28,
  type = 16
  },
  {
  lv = "300.0",
  offset = 148,
  type = 16
  },
  {
  lv = "13.0",
  offset = 164,
  type = 16
  },
  {
  lv = "8.0",
  offset = 192,
  type = 16
  }
}
qmxg = {
  {
  value = 0,
  offset = 0,
  type = 16
  },
  {
  value = 0,
  offset = 12,
  type = 16
  },
  {
  value = 0,
  offset = 28,
  type = 16
  },
  {
  value = 99999,
  offset = 148,
  type = 16
  },
  {
  value = 0,
  offset = 164,
  type = 16
  },
  {
  value = 0,
  offset = 192,
  type = 16
  }
}
xqmnb(qmnb)
end

function bzd()
qmnb = {
  {memory = 32},
  {
  name = "กึ่งอัตโนมัติ"
  },
  {value = 15, type = 16},
  {
  lv = "6.0",
  offset = 12,
  type = 16
  },
  {
  lv = "30.0",
  offset = 28,
  type = 16
  },
  {
  lv = "710.0",
  offset = 148,
  type = 16
  },
  {
  lv = "4.0",
  offset = 164,
  type = 16
  },
  {
  lv = "4.0",
  offset = 172,
  type = 16
  },
  {
  lv = "8.0",
  offset = 192,
  type = 16
  }
}
qmxg = {
  {
  value = 0,
  offset = 0,
  type = 16
  },
  {
  value = 0,
  offset = 12,
  type = 16
  },
  {
  value = 0,
  offset = 28,
  type = 16
  },
  {
  value = 99999,
  offset = 148,
  type = 16
  },
  {
  value = 0,
  offset = 164,
  type = 16
  },
  {
  value = 0,
  offset = 172,
  type = 16
  },
  {
  value = 0,
  offset = 192,
  type = 16
  }
}
xqmnb(qmnb)
end

function uzi()
qmnb = {
  {memory = 32},
  {name = "uzi"},
  {value = 16, type = 16},
  {
  lv = "2.0",
  offset = 12,
  type = 16
  },
  {
  lv = "30.0",
  offset = 28,
  type = 16
  },
  {
  lv = "320.0",
  offset = 148,
  type = 16
  },
  {
  lv = "4.0",
  offset = 164,
  type = 16
  },
  {
  lv = "4.0",
  offset = 172,
  type = 16
  },
  {
  lv = "5.0",
  offset = 192,
  type = 16
  }
}
qmxg = {
  {
  value = 0,
  offset = 0,
  type = 16
  },
  {
  value = 0,
  offset = 12,
  type = 16
  },
  {
  value = 0,
  offset = 28,
  type = 16
  },
  {
  value = 99999,
  offset = 148,
  type = 16
  },
  {
  value = 0,
  offset = 164,
  type = 16
  },
  {
  value = 0,
  offset = 172,
  type = 16
  },
  {
  value = 0,
  offset = 192,
  type = 16
  }
}
xqmnb(qmnb)
end

function smg()
qmnb = {
  {memory = 32},
  {name = "smg"},
  {value = 15, type = 16},
  {
  lv = "3.0",
  offset = 12,
  type = 16
  },
  {
  lv = "25.0",
  offset = 28,
  type = 16
  },
  {
  lv = "300.0",
  offset = 148,
  type = 16
  },
  {
  lv = "4.0",
  offset = 164,
  type = 16
  },
  {
  lv = "4.0",
  offset = 172,
  type = 16
  },
  {
  lv = "1.0",
  offset = 192,
  type = 16
  }
}
qmxg = {
  {
  value = 0,
  offset = 0,
  type = 16
  },
  {
  value = 0,
  offset = 12,
  type = 16
  },
  {
  value = 0,
  offset = 28,
  type = 16
  },
  {
  value = 99999,
  offset = 148,
  type = 16
  },
  {
  value = 0,
  offset = 164,
  type = 16
  },
  {
  value = 0,
  offset = 172,
  type = 16
  },
  {
  value = 0,
  offset = 192,
  type = 16
  }
}
xqmnb(qmnb)
end

function ptwh()
qmnb = {
  {memory = 32},
  {
  name = "ซอง"
  },
  {value = 15, type = 16},
  {
  lv = "3.0",
  offset = 12,
  type = 16
  },
  {
  lv = "10.0",
  offset = 40,
  type = 16
  },
  {
  lv = "4.0",
  offset = 112,
  type = 16
  },
  {
  lv = "4.0",
  offset = 116,
  type = 16
  },
  {
  lv = "2.799999952316284",
  offset = 120,
  type = 16
  },
  {
  lv = "40.0",
  offset = 148,
  type = 16
  }
}
qmxg = {
  {
  value = 0,
  offset = 0,
  type = 16
  },
  {
  value = 0,
  offset = 12,
  type = 16
  },
  {
  value = 0,
  offset = 40,
  type = 16
  },
  {
  value = 0,
  offset = 112,
  type = 16
  },
  {
  value = 0,
  offset = 116,
  type = 16
  },
  {
  value = 9999,
  offset = 148,
  type = 16
  }
}
xqmnb(qmnb)
end

function ldwh()
qmnb = {
  {memory = 32},
  {name = "ระเบิดมือ"},
  {value = 24, type = 16},
  {
  lv = "24.0",
  offset = 12,
  type = 16
  },
  {
  lv = "10.0",
  offset = 40,
  type = 16
  },
  {
  lv = "4.0",
  offset = 112,
  type = 16
  },
  {
  lv = "4.0",
  offset = 116,
  type = 16
  },
  {
  lv = "2.799999952316284",
  offset = 120,
  type = 16
  },
  {
  lv = "25.0",
  offset = 148,
  type = 16
  }
}
qmxg = {
  {
  value = 0,
  offset = 0,
  type = 16
  },
  {
  value = 0,
  offset = 12,
  type = 16
  },
  {
  value = 0,
  offset = 40,
  type = 16
  },
  {
  value = 0,
  offset = 112,
  type = 16
  },
  {
  value = 0,
  offset = 116,
  type = 16
  },
  {
  value = 9999,
  offset = 148,
  type = 16
  }
}
xqmnb(qmnb)
end

function lfkss()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("0.001953125;512;1;0.5;0.27000001073;0.60000002384", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("0.60000002384", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(1000)
gg.editAll("9999", gg.TYPE_FLOAT)
gg.clearList()
end

function qlss()
F = gg.alert("มองมุมสูง", "เปิด", "ปิด ","ยกเลิก")
if F == 1 then
gg.clearResults()
  gg.setRanges(32)
  gg.searchNumber("1.5;-40;80;-360;360;56;131072E;8;::90", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.searchNumber("1.5", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(100)
  gg.editAll("60", gg.TYPE_FLOAT)
  gg.toast("เปิด")
    elseif F == 2 then
   gg.clearResults()
  gg.setRanges(32)
  gg.searchNumber("1.5", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.searchNumber("1.5;-40;80;-360;360;56;131072E;8;::90", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(100)
  gg.editAll("60", gg.TYPE_FLOAT)
  gg.toast("ปิด")
end
end

function B1()
local L0_415, L1_416
L0_415, L1_416 = nil, nil
end

function B2()
F = gg.alert("ลบกำแพง", "เปิด", "ปิด ","ยกเลิก")
  if F == 1 then
  gg.clearResults()
  gg.setRanges(16384)
  gg.searchNumber("0.81399995089", gg.REGION_C_BSS, false, gg.SIGN_FUZZY_EQUAL, 0, -1)
  gg.searchNumber("0.81399995089", gg.REGION_C_BSS, false, gg.SIGN_FUZZY_EQUAL, 0, -1)
  gg.getResults(100)
  gg.editAll("10.123", gg.REGION_C_BSS)
  gg.toast("เปิด")
  gg.clearResults()
  elseif F == 2 then
  gg.clearResults()
  gg.setRanges(16384)
  gg.searchNumber("10.123", gg.REGION_C_BSS, false, gg.SIGN_FUZZY_EQUAL, 0, -1)
  gg.searchNumber("10.123", gg.REGION_C_BSS, false, gg.SIGN_FUZZY_EQUAL, 0, -1)
  gg.getResults(100)
  gg.editAll("0.81399995089", gg.REGION_C_BSS)
  gg.toast("ปิด")
  gg.clearResults()
end
end

function B3()
  F = gg.alert ("เสาบ้าน", "เปิด", "ปิด")
  if F == 1 then
gg.setRanges(gg.REGION_BAD)
gg.searchNumber("0.14822639525;4.0;0.74931889772;0.36428490281:25", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("4", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(100)
gg.editAll("999", gg.TYPE_FLOAT)
gg.toast("เปิด")
gg.clearResults()
gg.setRanges(gg.REGION_BAD)
gg.searchNumber("0.14822684228;4.0;-0.14822591841;4.0:69", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("4", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(100)
gg.editAll("999", gg.TYPE_FLOAT)
gg.toast("เปิด")
gg.clearResults()
gg.setRanges(gg.REGION_BAD)
gg.searchNumber("0.375;2.0;-0.15000064671;4.0;0.0;4.0;4.0;4.0:141", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("4", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(100)
gg.editAll("999", gg.TYPE_FLOAT)
gg.toast("เปิด")
elseif F == 2 then
gg.clearResults()
gg.setRanges(gg.REGION_BAD)
gg.searchNumber("0.14822639525;4.0;0.74931889772;0.36428490281:25", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("999", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(100)
gg.editAll("4", gg.TYPE_FLOAT)
gg.toast("เปิด")
gg.clearResults()
gg.setRanges(gg.REGION_BAD)
gg.searchNumber("0.14822684228;4.0;-0.14822591841;4.0:69", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("999", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(100)
gg.editAll("4", gg.TYPE_FLOAT)
gg.toast("เปิด")
gg.clearResults()
gg.setRanges(gg.REGION_BAD)
gg.searchNumber("0.375;2.0;-0.15000064671;4.0;0.0;4.0;4.0;4.0:141", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("999", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(100)
gg.editAll("4", gg.TYPE_FLOAT)
gg.toast("เปิด")
end
end

function B4()
  F = gg.alert("กลางวัน", "เปิด","ปิด")
  if F == 1 then
gg.clearList()
  gg.clearResults()
  gg.setRanges(4)
  gg.searchNumber("1,004,243,884D;9.2194229e-41;-1D::", 16,false,gg.SIGN_EQUAL,0, -1)
  gg.searchNumber("9.2194229e-41",16,false,gg.SIGN_EQUAL,0,-1)
  gg.getResults(1)
  gg.editAll("999",16)
  gg.clearList() 
  elseif F == 2 then
  gg.clearList()
  gg.clearResults()
  gg.setRanges(4)
  gg.searchNumber("1,004,243,884D;999;-1D::", 16,false,gg.SIGN_EQUAL,0, -1)
  gg.searchNumber("999",16,false,gg.SIGN_EQUAL,0,-1)
  gg.getResults(1)
  gg.editAll("9.2194229e-41",16)
  gg.clearList() 
  end
  end

function C1()
if KG[4] == 0 then
  gg.clearList()
  gg.clearResults()
  gg.setRanges(1048576)
  gg.searchNumber("16.0;3.0;2.0::52", 16, false, gg.SIGN_EQUAL, 0, -1)
  gg.searchNumber("2", 16, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(999)
  gg.editAll("999", 16)
  SS1()
else
  gg.clearList()
  gg.clearResults()
  gg.setRanges(1048576)
  gg.searchNumber("16.0;3.0;999.0::52", 16, false, gg.SIGN_EQUAL, 0, -1)
  gg.searchNumber("999", 16, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(999)
  gg.editAll("2", 16)
  SS2()
end
end

function C9()
  gg.clearResults()
  gg.setRanges(gg.REGION_VIDEO)
  gg.searchNumber("0.81484669447", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1, 0)
  gg.getResults(9999) 
  gg.editAll("999999999", gg.TYPE_FLOAT)
  gg.clearResults()
  gg.toast("เปลี่ยนสี")
  end

function C10()
  gg.clearResults()
  gg.setRanges(gg.REGION_VIDEO)
  gg.searchNumber("8204", gg.TYPE_DWORD, false, gg.SIGN_EQUAL, 0, -1, 0)
  gg.getResults(9999) 
  gg.editAll("9999999", gg.TYPE_DWORD)
  gg.clearResults()
  gg.toast("50%")
  gg.clearResults()
  gg.setRanges(gg.REGION_VIDEO)
  gg.searchNumber("8211", gg.TYPE_DWORD, false, gg.SIGN_EQUAL, 0, -1, 0)
  gg.getResults(9999) 
  gg.editAll("9999999", gg.TYPE_DWORD)
  gg.clearResults()
  gg.toast("เปลี่ยนสี")
  end

function C2()
F = gg.alert("เทคโนโลยี", "เสาอากาศสีน้ำเงิน" .. LTX, "เสาอากาศสีหลัก" .. TX)
if F == 1 then
  LSTX()
elseif F == 2 then
  YSTX()
end
end

function drxx()
qmnb = {
  {memory = 4},
  {name = "เสาอากาศ"},
  {value = 2.3234015600337443E-7, type = 16},
  {
  lv = 3.60133705331478E-43,
  offset = -4,
  type = 16
  },
  {
  lv = 1.422524746885756E-6,
  offset = 4,
  type = 16
  }
}
qmxg = {
  {
  value = -9999,
  offset = 0,
  type = 16
  }
}
xqmnb(qmnb)
end

function YSTX()
if KG[5] == 0 then
  qmnb = {
  {memory = 4},
  {name = "เสาอากาศ"},
  {value = 0.16947640478610992, type = 16},
  {
      lv = -0.16947640478610992,
      offset = 20,
      type = 16
  }
  }
  qmxg = {
  {
      value = -999999,
      offset = 0,
      type = 16
  }
  }
  xqmnb(qmnb)
  TX1()
else
  qmnb = {
  {memory = 4},
  {
      name = "ปิดเสาอากาศ"
  },
  {value = -999999, type = 16},
  {
      lv = -0.16947640478610992,
      offset = 20,
      type = 16
  }
  }
  qmxg = {
  {
      value = 0.16947640478610992,
      offset = 0,
      type = 16
  }
  }
  xqmnb(qmnb)
  TX2()
end
end

function LSTX()
if KG[14] == 0 then
  qmnb = {
  {memory = 4},
  {name = "เสาอากาศ"},
  {value = 0.16947640478610992, type = 16},
  {
      lv = -0.16947640478610992,
      offset = 20,
      type = 16
  }
  }
  qmxg = {
  {
      value = -999999,
      offset = 0,
      type = 16
  }
  }
  xqmnb(qmnb)
  LTX1()
else
  qmnb = {
  {memory = 4},
  {
      name = "ปิดเสาอากาศ"
  },
  {value = -999999, type = 16},
  {
      lv = -0.16947640478610992,
      offset = 20,
      type = 16
  }
  }
  qmxg = {
  {
      value = 0.16947640478610992,
      offset = 0,
      type = 16
  }
  }
  xqmnb(qmnb)
  LTX2()
end
end

function rwys()
if KG[15] == 0 then
  qmnb = {
  {memory = 32},
  {name = "ชิงทรัพย์"},
  {value = "84069", type = 4},
  {
      lv = "18",
      offset = -8,
      type = 4
  }
  }
  qmxg = {
  {
      value = 17,
      offset = -8,
      type = 4
  }
  }
  xqmnb(qmnb)
  RWYS1()
else
  qmnb = {
  {memory = 32},
  {name = "ชิงทรัพย์"},
  {value = "84069", type = 4},
  {
      lv = "17",
      offset = -8,
      type = 4
  }
  }
  qmxg = {
  {
      value = 18,
      offset = -8,
      type = 4
  }
  }
  xqmnb(qmnb)
  RWYS2()
end
end

function qtdg()
F = gg.alert("ขั้นที่ 1 เปิดหน้าlobby ขั้นที่ 2 เปิดในเซิฟ","ครั้งที่ 2","ครั้งที่ 1")
if F == 1 then
gg.clearList()
gg.clearResults()
gg.setRanges(4)
gg.searchNumber("1.03999996185", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(100)
gg.editAll("2.222222", gg.TYPE_FLOAT)
elseif F == 2 then
gg.clearList()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-7.1591722e24;-2.9687729e21;2;1;-1.3093038e25::", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("2", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(999)
gg.editAll("1.9", gg.TYPE_FLOAT)
gg.toast("เสร็จสิ้น")
end
end

function C3()
if KG[6] == 0 then
  qmnb = {
  {memory = 4},
  {name = "กลางวันและกลางคืน"},
  {
      value = "0.0066999997943639755",
      type = 16
  },
  {
      lv = "9.219422856485836E-41",
      offset = 8,
      type = 16
  }
  }
  qmxg = {
  {
      value = 999,
      offset = 8,
      type = 16
  }
  }
  xqmnb(qmnb)
  YS1()
else
  qmnb = {
  {memory = 4},
  {name = "กลางวันและกลางคืน"},
  {
      value = "0.0066999997943639755",
      type = 16
  },
  {
      lv = "999",
      offset = 8,
      type = 16
  }
  }
  qmxg = {
  {
      value = 9.219422856485836E-41,
      offset = 8,
      type = 16
  }
  }
  xqmnb(qmnb)
  YS2()
end
end

function C4()
if KG[7] == 0 then
  gg.clearList()
  gg.clearResults()
  gg.setRanges(1048576)
  gg.searchNumber("0.0;2.0;-1.0;1.17549435e-38::52", 16, false, gg.SIGN_EQUAL, 0, -1)
  gg.searchNumber("2", 16, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(999)
  gg.editAll("0", 16)
  LT1()
else
  gg.clearList()
  gg.clearResults()
  gg.setRanges(1048576)
  gg.searchNumber("0.0;0.0;-1.0;1.17549435e-38::52", 16, false, gg.SIGN_EQUAL, 0, -1)
  gg.searchNumber("0", 16, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(999)
  gg.editAll("2.25", 16)
  LT2()
end
end

function C5()
  if KG[9] == 0 then
    qmnb = {
      {memory = 1048576},
      {name = "ทำงาน"},
      {
        value = "2.250000238418579",
        type = 16
      },
      {
        lv = "1.1180834903756764E-19",
        offset = 4,
        type = 16
      }
    }
    qmxg = {
      {
        value = 0.2333,
        offset = 0,
        type = 16
      }
    }
    xqmnb(qmnb)
    qmnb = {
      {memory = 1048576},
      {name = "ทำงาน"},
      {
        value = "2.250000238418579",
        type = 16
      },
      {
        lv = "3.411825521566753E-29",
        offset = 4,
        type = 16
      }
    }
    qmxg = {
      {
        value = 0.233,
        offset = 0,
        type = 16
      }
    }
    xqmnb(qmnb)
    qmnb = {
      {memory = 1048576},
      {name = "ทำงาน"},
      {
        value = "2.250000238418579",
        type = 16
      },
      {
        lv = "5.837574911607241E-29",
        offset = 4,
        type = 16
      }
    }
    qmxg = {
      {
        value = 0.233,
        offset = 0,
        type = 16
      }
    }
    xqmnb(qmnb)
    XZ1()
  else
    qmnb = {
      {memory = 1048576},
      {name = "ทำงาน"},
      {value = "0.2333", type = 16},
      {
        lv = "1.1180834903756764E-19",
        offset = 4,
        type = 16
      }
    }
    qmxg = {
      {
        value = 2.250000238418579,
        offset = 0,
        type = 16
      }
    }
    xqmnb(qmnb)
    qmnb = {
      {memory = 1048576},
      {name = "ทำงาน"},
      {value = "0.2333", type = 16},
      {
        lv = "3.411825521566753E-29",
        offset = 4,
        type = 16
      }
    }
    qmxg = {
      {
        value = 2.250000238418579,
        offset = 0,
        type = 16
      }
    }
    xqmnb(qmnb)
    qmnb = {
      {memory = 1048576},
      {name = "ทำงาน"},
      {value = "0.2333", type = 16},
      {
        lv = "5.837574911607241E-29",
        offset = 4,
        type = 16
      }
    }
    qmxg = {
      {
        value = 2.250000238418579,
        offset = 0,
        type = 16
      }
    }
    xqmnb(qmnb)
    XZ2()
  end
end

function C6()
if KG[10] == 0 then
  gg.clearList()
  gg.clearResults()
  gg.setRanges(4)
  gg.searchNumber("16,261W;25W;161W  ;1W;1.03999996185", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.searchNumber("1.03999996185", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(100)
  gg.editAll("2.222222", gg.TYPE_FLOAT)
  DD1()
else
  gg.clearList()
  gg.clearResults()
  DD2()
end
end

function C7()
if KG[12] == 0 then
  gg.clearList()
  gg.clearResults()
  gg.setRanges(16384)
  gg.searchNumber("0.14177720249", 16, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(3)
  gg.editAll("0.1492135418", 16)
  gg.clearResults()
  gg.setRanges(16384)
  gg.searchNumber("6.30000019073", 16, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(999)
  gg.editAll("3.3157794", 16)
  WK1()
else
  gg.clearList()
  gg.clearResults()
  gg.setRanges(16384)
  gg.searchNumber("0.1492135418", 16, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(3)
  gg.editAll("0.14177720249", 16)
  gg.clearResults()
  gg.setRanges(16384)
  gg.searchNumber("3.3157794", 16, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(999)
  gg.editAll("6.30000019073", 16)
  WK2()
end
end

function C8()
  F = gg.alert("มุมมองไกล", "เปิด","ปิด")
  if F == 1 then
  gg.clearResults()
  gg.setRanges(gg.REGION_ANONYMOUS)
  gg.searchNumber("1.7", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.refineNumber("1.7", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(2000)
  gg.editAll("50.123123", gg.TYPE_FLOAT)
  gg.clearResults()
  gg.processResume()
  gg.clearList()
  elseif F == 2 then
  gg.clearResults()
  gg.setRanges(gg.REGION_ANONYMOUS)
  gg.searchNumber("50.123123", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(2000)
  gg.editAll("1.7", gg.TYPE_FLOAT)
  gg.clearResults()
  gg.processResume()
  gg.clearList()
  end
  end

function stcq()
  F = gg.alert("เปิดบนเรือขนสินค้า", "เปิด","ปิด","ยกเลิก")
  if F == 1 then
gg.clearResults()
gg.setRanges(4)
gg.searchNumber("1.0F;0.00999999978F;3.7835059e-43F;4.2038954e-45F;10,000.0F;10,000.001953125F", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("10000", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_FLOAT)
gg.toast("ทะลุกำแพง เปิด")
  elseif F == 2 then  
gg.clearResults()
gg.setRanges(4)
gg.searchNumber("1.0F;0.00999999978F;3.7835059e-43F;4.2038954e-45F;0F;10,000.001953125F", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("0", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(9999)
gg.editAll("10000", gg.TYPE_FLOAT)
gg.toast("ทะลุกำแพง ปิด")
end
end

function E1()
qmnb = {
  {memory = 16384},
  {name = "ใต้ดิน"},
  {value = "2.0", type = 16},
  {
  lv = "-2.0",
  offset = 4,
  type = 16
  },
  {
  lv = "2.0",
  offset = 8,
  type = 16
  },
  {
  lv = "0.0",
  offset = 12,
  type = 16
  },
  {
  lv = "1.0",
  offset = 24,
  type = 16
  },
  {
  lv = "1.0",
  offset = 36,
  type = 16
  },
  {
  lv = "1.0",
  offset = 48,
  type = 16
  }
}
qmxg = {
  {
  value = 1.87,
  offset = 0,
  type = 16
  },
  {
  value = 1.87,
  offset = 8,
  type = 16
  }
}
xqmnb(qmnb)
end

function E2()
qmnb = {
  {memory = 16384},
  {name = "ใต้ดิน"},
  {value = "2.0", type = 16},
  {
  lv = "-2.0",
  offset = 4,
  type = 16
  },
  {
  lv = "2.0",
  offset = 8,
  type = 16
  },
  {
  lv = "0.0",
  offset = 12,
  type = 16
  },
  {
  lv = "1.0",
  offset = 24,
  type = 16
  },
  {
  lv = "1.0",
  offset = 36,
  type = 16
  },
  {
  lv = "1.0",
  offset = 48,
  type = 16
  }
}
qmxg = {
  {
  value = 1.91,
  offset = 0,
  type = 16
  },
  {
  value = 1.91,
  offset = 8,
  type = 16
  }
}
xqmnb(qmnb)
end

function E3()
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("16,261W;25W;161W;1W;1.03999996185", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("1.03999996185", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(10000)
jg = gg.getResults(100)
sl = gg.getResultCount()
if 100 < sl then
  sl = 100
end
for _FORV_3_ = 1, sl do
  dzy = jg[_FORV_3_].address
  gg.addListItems({
  [1] = {
      address = dzy,
      flags = gg.TYPE_FLOAT,
      freeze = true,
      value = 1.5
  }
  })
end
gg.clearResults()
end

function zdct()
  gg.clearList()
  gg.clearResults()
  gg.setRanges(gg.REGION_C_ALLOC)
  gg.searchNumber("0.11000000000~0.11000090000", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.searchNumber("0.11000000000~0.11000090000", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(999)
  gg.editAll("5.5", gg.TYPE_FLOAT)
  gg.clearList()
  gg.clearResults()
  gg.toast("[ฟันไกล เปิด]")
  end

function djft()
F = gg.alert("คำแนะนำ : ใช้ฐานก่อนสร้างในการบิน", "เปิด", "ปิด")
if F == 1 then
  yi()
elseif F == 2 then
  yj()
end
end

function adgasd()
F = gg.alert("กระสุนทะลุกำแพง : ต้องอยู่บนเพด้าน", "เปิด", "ปิด")
  if F == 1 then
  ye()
  elseif F == 2 then
  yf()
  end
  end
  function asdfg()
  qmnb = {
    {memory = 32},
    {name = " "},
    {value = 0.10000000149011612, type = 16},
    {
      lv = 6.699999809265137,
      offset = -16,
      type = 16
    },
    {
      lv = 0.009999999776482582,
      offset = 4,
      type = 16
    },
    {
      lv = 0.10000000149011612,
      offset = 8,
      type = 16
    }
  }
  qmxg = {
    {
      value = -999,
      offset = 0,
      type = 16
    },
    {
      value = -999,
      offset = 8,
      type = 16
    }
  }
  xqmnb(qmnb)
  qmnb = {
    {memory = 4},
    {name = " "},
    {value = 1.0000000331813535E32, type = 16},
    {
      lv = 0.10000000149011612,
      offset = -4,
      type = 16
    },
    {
      lv = 0.004999999888241291,
      offset = 4,
      type = 16
    },
    {
      lv = 0.0024999999441206455,
      offset = 8,
      type = 16
    },
    {
      lv = 0.3999999761581421,
      offset = 12,
      type = 16
    }
  }
  qmxg = {
    {
      value = 8.88479995728,
      offset = 0,
      type = 16
    }
  }
  xqmnb(qmnb)
end


function ye()
gg.setRanges(4)
for _FORV_3_ = 1, 1 do
  if gg.isVisible(true) then
  gg.setRanges(4)
  SearchWrite({
      {"5.303", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"10", 16}
  }, 16)
  gg.clearResults()
  gg.setRanges(4)
  SearchWrite({
      {"10", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"10", 16}
  }, 16)
  gg.clearResults()
  gg.setRanges(4)
  SearchWrite({
      {"9.098", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"10", 16}
  }, 16)
  gg.clearResults()
  do return end
  return
  end
  for _FORV_7_ = 1, 1 do
  if gg.isVisible(true) then
      gg.setRanges(4)
      SearchWrite({
      {"5.303", 0},
      {"7", -16},
      {"8", 32}
      }, {
      {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
      {"10", 0},
      {"7", -16},
      {"8", 32}
      }, {
      {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
      {"9.098", 0},
      {"7", -16},
      {"8", 32}
      }, {
      {"10", 16}
      }, 16)
      gg.clearResults()
      do return end
      return
  end
  SearchWrite({
      {"30", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"0.5", 16}
  }, 16)
  gg.clearResults()
  gg.setRanges(16440)
  gg.setRanges(16444)
  for _FORV_11_ = 1, 1 do
      if gg.isVisible(true) then
      gg.setRanges(4)
      SearchWrite({
          {"5.303", 0},
          {"7", -16},
          {"8", 32}
      }, {
          {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
          {"10", 0},
          {"7", -16},
          {"8", 32}
      }, {
          {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
          {"9.098", 0},
          {"7", -16},
          {"8", 32}
      }, {
          {"10", 16}
      }, 16)
      gg.clearResults()
      do return end
      return
      end
      for _FORV_15_ = 1, 1 do
      if gg.isVisible(true) then
          gg.setRanges(4)
          SearchWrite({
          {"5.30Ⅰ3", 0},
          {"7", -16},
          {"8", 32}
          }, {
          {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
          {"10", 0},
          {"7", -16},
          {"8", 32}
          }, {
          {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
          {"9.098", 0},
          {"7", -16},
          {"8", 32}
          }, {
          {"10", 16}
          }, 16)
          gg.clearResults()
          do return end
          return
      end
      SearchWrite({
          {"1Ⅰ0000", 0},
          {"10000", 12},
          {"100", 4}
      }, {
          {"0", 16}
      }, 84)
      gg.setRanges(4)
      for _FORV_19_ = 1, 1 do
          if gg.isVisible(true) then
          gg.setRanges(4)
          SearchWrite({
              {"5.303", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
              {"10", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
              {"9.098", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"10", 16}
          }, 16)
          gg.clearResults()
          do return end
          return
          end
          for _FORV_23_ = 1, 1 do
          if gg.isVisible(true) then
              gg.setRanges(4)
              SearchWrite({
              {"5.303", 0},
              {"7", -16},
              {"8", 32}
              }, {
              {"10", 16}
              }, 16)
              gg.clearResults()
              gg.setRanges(4)
              SearchWrite({
              {"10", 0},
              {"7", -16},
              {"8", 32}
              }, {
              {"10", 16}
              }, 16)
              gg.clearResults()
              gg.setRanges(4)
              SearchWrite({
              {"9.098", 0},
              {"7", -16},
              {"8", 32}
              }, {
              {"10", 16}
              }, 16)
              gg.clearResults()
              do return end
              return
          end
          SearchWrite({
              {"21.08", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"1.1", 16}
          }, 16)
          gg.clearResults()
          end
      end
      end
  end
  end
end
end

function yf()
gg.setRanges(4)
for _FORV_3_ = 1, 1 do
  if gg.isVisible(true) then
  gg.setRanges(4)
  SearchWrite({
      {"20.303", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"10", 16}
  }, 16)
  gg.clearResults()
  gg.setRanges(4)
  SearchWrite({
      {"16.09", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"10", 16}
  }, 16)
  gg.clearResults()
  gg.setRanges(4)
  SearchWrite({
      {"7.098", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"10", 16}
  }, 16)
  gg.clearResults()
  do return end
  return
  end
  for _FORV_7_ = 1, 1 do
  if gg.isVisible(true) then
      gg.setRanges(4)
      SearchWrite({
      {"20.303", 0},
      {"7", -16},
      {"8", 32}
      }, {
      {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
      {"16.09", 0},
      {"7", -16},
      {"8", 32}
      }, {
      {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
      {"7.098", 0},
      {"7", -16},
      {"8", 32}
      }, {
      {"10", 16}
      }, 16)
      gg.clearResults()
      do return end
      return
  end
  SearchWrite({
      {"9.0785", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"0.05556", 16}
  }, 16)
  gg.clearResults()
  gg.setRanges(16440)
  gg.setRanges(16444)
  for _FORV_11_ = 1, 1 do
      if gg.isVisible(true) then
      gg.setRanges(4)
      SearchWrite({
          {"20.303", 0},
          {"7", -16},
          {"8", 32}
      }, {
          {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
          {"16.09", 0},
          {"7", -16},
          {"8", 32}
      }, {
          {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
          {"7.098", 0},
          {"7", -16},
          {"8", 32}
      }, {
          {"10", 16}
      }, 16)
      gg.clearResults()
      do return end
      return
      end
      for _FORV_15_ = 1, 1 do
      if gg.isVisible(true) then
          gg.setRanges(4)
          SearchWrite({
          {"20.303", 0},
          {"7", -16},
          {"8", 32}
          }, {
          {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
          {"16.09", 0},
          {"7", -16},
          {"8", 32}
          }, {
          {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
          {"7.098", 0},
          {"7", -16},
          {"8", 32}
          }, {
          {"10", 16}
          }, 16)
          gg.clearResults()
          do return end
          return
      end
      SearchWrite({
          {"1Ⅰ0000", 0},
          {"10000", 12},
          {"100", 4}
      }, {
          {"5Ⅰ000", 16}
      }, 84)
      gg.setRanges(4)
      for _FORV_19_ = 1, 1 do
          if gg.isVisible(true) then
          gg.setRanges(4)
          SearchWrite({
              {"20.303", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
              {"16.09", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
              {"7.098", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"10", 16}
          }, 16)
          gg.clearResults()
          do return end
          return
          end
          for _FORV_23_ = 1, 1 do
          if gg.isVisible(true) then
              gg.setRanges(4)
              SearchWrite({
              {"20.303", 0},
              {"7", -16},
              {"8", 32}
              }, {
              {"10", 16}
              }, 16)
              gg.clearResults()
              gg.setRanges(4)
              SearchWrite({
              {"16.09", 0},
              {"7", -16},
              {"8", 32}
              }, {
              {"10", 16}
              }, 16)
              gg.clearResults()
              gg.setRanges(4)
              SearchWrite({
              {"7.098", 0},
              {"7", -16},
              {"8", 32}
              }, {
              {"10", 16}
              }, 16)
              gg.clearResults()
              do return end
              return
          end
          SearchWrite({
              {"16", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"20", 16}
          }, 16)
          gg.clearResults()
          end
      end
      end
  end
  end
end
end

function yi()
gg.setRanges(4)
for _FORV_3_ = 1, 1 do
  if gg.isVisible(true) then
  gg.setRanges(4)
  SearchWrite({
      {"39.093", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"10", 16}
  }, 16)
  gg.clearResults()
  gg.setRanges(4)
  SearchWrite({
      {"27.05190", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"10", 16}
  }, 16)
  gg.clearResults()
  gg.setRanges(4)
  SearchWrite({
      {"7.01609", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"10", 16}
  }, 16)
  gg.clearResults()
  do return end
  return
  end
  for _FORV_7_ = 1, 1 do
  if gg.isVisible(true) then
      gg.setRanges(4)
      SearchWrite({
      {"39.093", 0},
      {"7", -16},
      {"8", 32}
      }, {
      {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
      {"27.05190", 0},
      {"7", -16},
      {"8", 32}
      }, {
      {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
      {"7.01609", 0},
      {"7", -16},
      {"8", 32}
      }, {
      {"10", 16}
      }, 16)
      gg.clearResults()
      do return end
      return
  end
  SearchWrite({
      {"4.5009856", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"9.80984", 16}
  }, 16)
  gg.clearResults()
  gg.setRanges(16440)
  gg.setRanges(16444)
  for _FORV_11_ = 1, 1 do
      if gg.isVisible(true) then
      gg.setRanges(4)
      SearchWrite({
          {"39.093", 0},
          {"7", -16},
          {"8", 32}
      }, {
          {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
          {"27.05190", 0},
          {"7", -16},
          {"8", 32}
      }, {
          {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
          {"7.01609", 0},
          {"7", -16},
          {"8", 32}
      }, {
          {"10", 16}
      }, 16)
      gg.clearResults()
      do return end
      return
      end
      for _FORV_15_ = 1, 1 do
      if gg.isVisible(true) then
          gg.setRanges(4)
          SearchWrite({
          {"39.093", 0},
          {"7", -16},
          {"8", 32}
          }, {
          {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
          {"27.05190", 0},
          {"7", -16},
          {"8", 32}
          }, {
          {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
          {"7.01609", 0},
          {"7", -16},
          {"8", 32}
          }, {
          {"10", 16}
          }, 16)
          gg.clearResults()
          do return end
          return
      end
      SearchWrite({
          {
          "2139095Ⅰ039",
          0
          },
          {"24008", 12}
      }, {
          {"0", 36}
      }, 84)
      gg.setRanges(16440)
      gg.setRanges(16444)
      for _FORV_19_ = 1, 1 do
          if gg.isVisible(true) then
          gg.setRanges(4)
          SearchWrite({
              {"39.093", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
              {"27.05190", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
              {"7.01609", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"10", 16}
          }, 16)
          gg.clearResults()
          do return end
          return
          end
          for _FORV_23_ = 1, 1 do
          if gg.isVisible(true) then
              gg.setRanges(4)
              SearchWrite({
              {"39.093", 0},
              {"7", -16},
              {"8", 32}
              }, {
              {"10", 16}
              }, 16)
              gg.clearResults()
              gg.setRanges(4)
              SearchWrite({
              {"27.05190", 0},
              {"7", -16},
              {"8", 32}
              }, {
              {"10", 16}
              }, 16)
              gg.clearResults()
              gg.setRanges(4)
              SearchWrite({
              {"7.01609", 0},
              {"7", -16},
              {"8", 32}
              }, {
              {"10", 16}
              }, 16)
              gg.clearResults()
              do return end
              return
          end
          SearchWrite({
              {
              "213909Ⅰ5039",
              0
              },
              {"24004", 12}
          }, {
              {"0", 36}
          }, 84)
          gg.setRanges(16440)
          gg.setRanges(16444)
          for _FORV_27_ = 1, 1 do
              if gg.isVisible(true) then
              gg.setRanges(4)
              SearchWrite({
                  {"39.093", 0},
                  {"7", -16},
                  {"8", 32}
              }, {
                  {"10", 16}
              }, 16)
              gg.clearResults()
              gg.setRanges(4)
              SearchWrite({
                  {"27.05190", 0},
                  {"7", -16},
                  {"8", 32}
              }, {
                  {"10", 16}
              }, 16)
              gg.clearResults()
              gg.setRanges(4)
              SearchWrite({
                  {"7.01609", 0},
                  {"7", -16},
                  {"8", 32}
              }, {
                  {"10", 16}
              }, 16)
              gg.clearResults()
              do return end
              return
              end
              for _FORV_31_ = 1, 1 do
              if gg.isVisible(true) then
                  gg.setRanges(4)
                  SearchWrite({
                  {"39.093", 0},
                  {"7", -16},
                  {"8", 32}
                  }, {
                  {"10", 16}
                  }, 16)
                  gg.clearResults()
                  gg.setRanges(4)
                  SearchWrite({
                  {"27.05190", 0},
                  {"7", -16},
                  {"8", 32}
                  }, {
                  {"10", 16}
                  }, 16)
                  gg.clearResults()
                  gg.setRanges(4)
                  SearchWrite({
                  {"7.01609", 0},
                  {"7", -16},
                  {"8", 32}
                  }, {
                  {"10", 16}
                  }, 16)
                  gg.clearResults()
                  do return end
                  return
              end
              SearchWrite({
                  {
                  "213909Ⅰ5039",
                  0
                  },
                  {"24000", 12}
              }, {
                  {"0", 36}
              }, 84)
              gg.setRanges(4)
              for _FORV_35_ = 1, 1 do
                  if gg.isVisible(true) then
                  gg.setRanges(4)
                  SearchWrite({
                      {"39.093", 0},
                      {"7", -16},
                      {"8", 32}
                  }, {
                      {"10", 16}
                  }, 16)
                  gg.clearResults()
                  gg.setRanges(4)
                  SearchWrite({
                      {"27.05190", 0},
                      {"7", -16},
                      {"8", 32}
                  }, {
                      {"10", 16}
                  }, 16)
                  gg.clearResults()
                  gg.setRanges(4)
                  SearchWrite({
                      {"7.01609", 0},
                      {"7", -16},
                      {"8", 32}
                  }, {
                      {"10", 16}
                  }, 16)
                  gg.clearResults()
                  do return end
                  return
                  end
                  for _FORV_39_ = 1, 1 do
                  if gg.isVisible(true) then
                      gg.setRanges(4)
                      SearchWrite({
                      {"39.093", 0},
                      {"7", -16},
                      {"8", 32}
                      }, {
                      {"10", 16}
                      }, 16)
                      gg.clearResults()
                      gg.setRanges(4)
                      SearchWrite({
                      {"27.05190", 0},
                      {"7", -16},
                      {"8", 32}
                      }, {
                      {"10", 16}
                      }, 16)
                      gg.clearResults()
                      gg.setRanges(4)
                      SearchWrite({
                      {"7.01609", 0},
                      {"7", -16},
                      {"8", 32}
                      }, {
                      {"10", 16}
                      }, 16)
                      gg.clearResults()
                      do return end
                      return
                  end
                  SearchWrite({
                      {"3.0350", 0},
                      {"7", -16},
                      {"8", 32}
                  }, {
                      {"7.092", 16}
                  }, 16)
                  gg.clearResults()
                  end
              end
              end
          end
          end
      end
      end
  end
  end
end
end

function yj()
gg.setRanges(4)
for _FORV_3_ = 1, 1 do
  if gg.isVisible(true) then
  gg.setRanges(4)
  SearchWrite({
      {"7.043", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"10", 16}
  }, 16)
  gg.clearResults()
  gg.setRanges(4)
  SearchWrite({
      {
      "26.03555190",
      0
      },
      {"7", -16},
      {"8", 32}
  }, {
      {"10", 16}
  }, 16)
  gg.clearResults()
  gg.setRanges(4)
  SearchWrite({
      {"17.0561609", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"10", 16}
  }, 16)
  gg.clearResults()
  do return end
  return
  end
  for _FORV_7_ = 1, 1 do
  if gg.isVisible(true) then
      gg.setRanges(4)
      SearchWrite({
      {"7.043", 0},
      {"7", -16},
      {"8", 32}
      }, {
      {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
      {
          "26.03555190",
          0
      },
      {"7", -16},
      {"8", 32}
      }, {
      {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
      {"17.0561609", 0},
      {"7", -16},
      {"8", 32}
      }, {
      {"10", 16}
      }, 16)
      gg.clearResults()
      do return end
      return
  end
  SearchWrite({
      {"2881", 0},
      {"7", -16},
      {"8", 32}
  }, {
      {"0", 16}
  }, 16)
  gg.clearResults()
  gg.setRanges(16440)
  gg.setRanges(16440)
  for _FORV_11_ = 1, 1 do
      if gg.isVisible(true) then
      gg.setRanges(4)
      SearchWrite({
          {"7.043", 0},
          {"7", -16},
          {"8", 32}
      }, {
          {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
          {
          "26.03555190",
          0
          },
          {"7", -16},
          {"8", 32}
      }, {
          {"10", 16}
      }, 16)
      gg.clearResults()
      gg.setRanges(4)
      SearchWrite({
          {"17.0561609", 0},
          {"7", -16},
          {"8", 32}
      }, {
          {"10", 16}
      }, 16)
      gg.clearResults()
      do return end
      return
      end
      for _FORV_15_ = 1, 1 do
      if gg.isVisible(true) then
          gg.setRanges(4)
          SearchWrite({
          {"7.043", 0},
          {"7", -16},
          {"8", 32}
          }, {
          {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
          {
              "26.03555190",
              0
          },
          {"7", -16},
          {"8", 32}
          }, {
          {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
          {"17.0561609", 0},
          {"7", -16},
          {"8", 32}
          }, {
          {"10", 16}
          }, 16)
          gg.clearResults()
          do return end
          return
      end
      SearchWrite({
          {"2Ⅰ57", 0},
          {"4", -4}
      }, {
          {"0", 32}
      }, 84)
      gg.setRanges(4)
      for _FORV_19_ = 1, 1 do
          if gg.isVisible(true) then
          gg.setRanges(4)
          SearchWrite({
              {"7.043", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
              {
              "26.03555190",
              0
              },
              {"7", -16},
              {"8", 32}
          }, {
              {"10", 16}
          }, 16)
          gg.clearResults()
          gg.setRanges(4)
          SearchWrite({
              {"17.0561609", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"10", 16}
          }, 16)
          gg.clearResults()
          do return end
          return
          end
          for _FORV_23_ = 1, 1 do
          if gg.isVisible(true) then
              gg.setRanges(4)
              SearchWrite({
              {"7.043", 0},
              {"7", -16},
              {"8", 32}
              }, {
              {"10", 16}
              }, 16)
              gg.clearResults()
              gg.setRanges(4)
              SearchWrite({
              {
                  "26.03555190",
                  0
              },
              {"7", -16},
              {"8", 32}
              }, {
              {"10", 16}
              }, 16)
              gg.clearResults()
              gg.setRanges(4)
              SearchWrite({
              {"17.0561609", 0},
              {"7", -16},
              {"8", 32}
              }, {
              {"10", 16}
              }, 16)
              gg.clearResults()
              do return end
              return
          end
          SearchWrite({
              {"150.086", 0},
              {"7", -16},
              {"8", 32}
          }, {
              {"67", 16}
          }, 16)
          gg.clearResults()
          end
      end
      end
  end
  end
end
end

function yk()
      if ssxz == gngb then
      ssxz = gnkq
      gg.alert("เปิดเสร้จแล้ว เดินลงจากเรือเดินไปฝั่ง \nถึงฝั่งแล้วเปิดฟังชั้นนี้อีกรอบ")
      gg.setRanges(4)
      SearchWrite({
      {
      1.0E32,
      0
      },
      {
      49,
      20
      },
      {
      999,
      32
      }
      }, {
      {
      0.37,
      -8,
      true
      }
      }, 16)
      gg.setRanges(16384)
      SearchWrite({
      {
      0.50291442871,
      0
      },
      {
      1,
      4
      },
      {
      1.00999999046,
      28
      }
      }, {
      {
      0.10000000149,
      4,
      false
      }
      }, 16)
      gg.toast("เดินบนน้ำ เปิด")
      elseif gnkq then
      gg.clearList()
      gg.clearResults()
      gg.setRanges(16384)
      SearchWrite({
      {
      0.50291442871,
      0
      },
      {
      0.10000000149,
      4
      },
      {
      1.00999999046,
      28
      }
      }, {
      {
      1,
      4,
      false
      }
      }, 16)
      gg.toast("ปิด")
      ssxz = gngb
      end
      end

function exit()
print(os.date("╭━[✯ Script By @SpaceX_Lios ✯]\n╰╮Time : %d/%m/%y | %X \n┏┻[Status: Working]\n┗[Subscribe Channel Devil Heaven]\n"))
gg.setVisible(true)
os.exit()
end

cs = "╭━[✯ Script By @SpaceX_Lios ✯]\n╰╮Time : %d/%m/%y | %X \n┏┻[Status: Working]\n┗[Subscribe Channel Devil Heaven]\n"
while true do
if gg.isVisible(true) then
  XGCK = 1
  gg.setVisible(false)
end
gg.clearResults()
if XGCK == 1 then
  index()
end
end
