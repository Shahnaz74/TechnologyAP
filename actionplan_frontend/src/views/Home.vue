<template>
  <div class=" h-screen">
    <!-- header -->
   <div class=" bg-white h-[10vh] top-0 drop-shadow-md">
    <div class=" grid grid-cols-2">
      <div class=" col-span-1">
        <img class=" md:ml-32 h-[8vh] my-[1vh]" src="@\assets\logo01.png" alt="">
      </div>
      <div class="col-span-1 hidden md:flex items-center">
        <p class="font-semibold text-sm">An initative of:</p>
        <img class=" h-[6vh] my-[2vh]" src="@\assets\logo03.png" alt="">
        <div class=" border-l border-slate-400 h-[6vh] my-[2vh]"></div>
        <img class=" h-[6vh] my-[2vh]" src="@\assets\logo02.png" alt="">
      </div>
    </div>
   </div>

    <!-- body -->
    <div v-if="page==1" class=" h-[82vh] bg-gradient-to-b from-[#F4F1EC] to-[#E6EBF1]">
      <div class="grid grid-cols-8 h-full">
        <div class=" col-span-1 "></div>
        <div class=" col-span-3 text-left mt-[20vh] ">
          <p class=" lg:text-3xl md:text-2xl font-bold mb-[2vh] text-black">Empowering individuals and their families at high cancer risk due to a gene fault</p>
          <p class=" border-2 border-orange-600 mb-[2vh] w-[10vh]"></p>
          <p class=" lg:text-lg md:text-base font-thin text-black">It can be daunting to be told that you have a fault in a gene which increases your risk of developing breast and/or ovarian cancer. If you are uncertain where to find information about managing your increased cancer risk, or what questions to ask your specialist, this website is here to help you.</p>
        </div>
        <div class=" col-span-2 mt-[30vh]">
          <button @click="page=2" class=" py-3 px-5 md:text-xl lg:text-2xl text-white bg-purple-700 hover:bg-purple-600 rounded hover:scale-105">Create Your Actionplan →</button>
        </div>
      </div>
    </div>

    <div v-else-if="page==2" class=" h-[82vh] bg-gradient-to-b from-[#51287B] to-[#093963]">
      <div class="h-full flex justify-center">
        <div class="mt-[20vh]">
          <p class="mb-[3vh] text-[#F7931E] font-bold">QUESTION 1</p>
          <p class="mb-[3vh] text-white text-2xl font-bold">Which gene did you test positive to?</p>
          <div class="mb-[3vh]" role="group">
            <button @click="option1=true; option3=false; option4=false; optionSelect=true" type="button" :class="{ activeOp: option1 }" class=" text-slate-800 drop-shadow hover:text-white py-5 px-24 font-bold bg-white hover:bg-[#623093] mx-2 rounded">BRCA1</button>
            <button @click="option1=false; option3=true; option4=false; optionSelect=true" type="button" :class="{ activeOp: option3 }" class=" text-slate-800 drop-shadow hover:text-white py-5 px-24 font-bold bg-white hover:bg-[#623093] mx-2 rounded">BRCA2</button>
            <button @click="option1=false; option3=false; option4=true; optionSelect=true" type="button" :class="{ activeOp: option4 }" class=" text-slate-800 drop-shadow hover:text-white py-5 px-24 font-bold bg-white hover:bg-[#623093] mx-2 rounded">PALB2</button>
          </div>
          <div class="mb-[3vh]">
            <button @click="page=3;Page02()" :disabled="!optionSelect" class="drop-shadow text-white py-4 px-16 font-bold bg-[#623093] disabled:text-slate-400 disabled:bg-slate-800 mx-2 rounded hover:scale-105">NEXT →</button>
          </div>
        </div>
      </div>
    </div>

    <div v-else-if="page==3" class=" h-[82vh] bg-gradient-to-b from-[#51287B] to-[#093963]">
      <div class="h-full flex justify-center">
        <div class="mt-[20vh]">
          <p class="mb-[3vh] text-[#F7931E] font-bold">QUESTION 2</p>
          <p class="mb-[3vh] text-white text-2xl font-bold">What is your current age?</p>
          <div class="mb-[2vh]" >
            <input v-model="ageV" type="number" class=" text-center rounded py-5 px-10 font-bold">
          </div>
          <div class="mb-[2vh]" >
            <p class=" text-white">*age must be between 20 to 80 years</p>
          </div>
          <div class="mb-[3vh]">
            <button @click="page=2" class="drop-shadow text-white py-4 px-16 font-bold bg-[#3D393E] hover:bg-[#007DBC] mx-2 rounded hover:scale-105">← BACK</button>
            <button @click="page=4;ChageAge()" :disabled="ageV=='' || ageV<20 || ageV>80" class="drop-shadow text-white py-4 px-16 font-bold bg-[#623093] disabled:text-slate-400 disabled:bg-slate-800 mx-2 rounded hover:scale-105">NEXT →</button>
          </div>
        </div>
      </div>
    </div>

    <div v-else-if="page==4" class=" h-[82vh] bg-gradient-to-b from-[#51287B] to-[#093963]">
      <div class="h-full flex justify-center">
        <div class="mt-[20vh]">
          <p class="mb-[3vh] text-[#F7931E] font-bold">QUESTION 3</p>
          <p class="mb-[1vh] text-white text-2xl font-bold">Which best describes you?</p>
          <p class="mb-[3vh] w-[40vw] text-white text-sm ">This question will not affect the information in your ActionPlan. It will be used purely for analytical purposes and guide the development of future content.</p>
          <div class="mb-[3vh]" role="group">
            <div>
              <button @click="option11=true; option22=false; optionSelect2=true" type="button" :class="{ activeOp2: option11 }" class=" text-slate-800 drop-shadow hover:text-white py-5 px-24 font-bold bg-white hover:bg-[#623093] mb-3 rounded">I'm exploring info for myself or someone I know with a gene fault</button>
            </div>
            <div>
              <button @click="option11=false; option22=true; optionSelect2=true" type="button" :class="{ activeOp2: option22 }" class=" text-slate-800 drop-shadow hover:text-white py-5 px-24 font-bold bg-white hover:bg-[#623093]  rounded">I'm a doctor providing support to my patient</button>
            </div>
          </div>
          <div class="mb-[3vh]">
            <button @click="page=3" class="drop-shadow text-white py-4 px-16 font-bold bg-[#3D393E] hover:bg-[#007DBC] mx-2 rounded hover:scale-105">← BACK</button>
            <button @click="page=5" :disabled="!optionSelect2" class="drop-shadow text-white py-4 px-16 font-bold bg-[#623093] disabled:text-slate-400 disabled:bg-slate-800 mx-2 rounded hover:scale-105">FINISH →</button>
          </div>
        </div>
      </div>
    </div>

    <div v-else-if="page==5" class=" min-h-[82vh] bg-[#D9EBFC]">
        <div class="grid grid-cols-8">
          <div class=" col-span-8 pt-[4vh] pb-[3vh] bg-gradient-to-b from-[#51287B] to-[#093963]">
            <div class=" grid grid-cols-8">
              <div class=" col-span-1"></div>
              <div class=" col-span-4 pr-20">
                 <p class=" text-white text-4xl border-b-2 w-fit border-[#E16326] mb-4">Here is your ActionPlan</p>
                 <p class=" text-slate-200 text-left my-4">The aim of this ActionPlan is to support you and help you manage your cancer risk. The information provided represents the risk and risk management recommendations for the average person who has your gene fault. Individual risks may differ.</p>
                 <p class=" text-slate-200 text-left my-4">If you have any specific questions or concerns about your circumstances, please discuss them with your specialist or contact your local familial cancer centre. People who have been diagnosed with a breast or ovarian cancer should discuss their care with their treating specialists.</p>
              </div>
              <div class=" col-span-2 flex justify-end gap-2">
                <div class="p-5 bg-gradient-to-r from-[#00C0BC] to-[#0074BC] rounded drop-shadow h-[120px]">
                  <p class="  text-white text-left text-sm font-bold">GENE FAULT <span @click="modalGraph=true" class=" font-thin ml-10 underline cursor-pointer hover:text-orange-300 text-xs">Edit</span></p>
                  <p v-if="option1" class="  text-white text-left text-3xl mt-4">BRCA1</p>
                  <p v-if="option3" class="  text-white text-left text-3xl mt-4">BRCA2</p>
                  <p v-if="option4" class="  text-white text-left text-3xl mt-4">PALB2</p>
                </div>
                <div class="p-5 bg-gradient-to-r from-[#00C0BC] to-[#0074BC] rounded drop-shadow h-[120px]">
                  <p class="  text-white text-left text-sm font-bold">AGE <span  @click="modalAge=true;ageV2=ageV" class=" font-thin ml-10 underline cursor-pointer hover:text-orange-300 text-xs">Edit</span></p>
                  <p class="  text-white text-left text-3xl mt-4">{{ageV}}</p>
                </div>
              </div>
              <div class=" col-span-1"></div>
            </div>
          </div>
          <div class=" col-span-1"></div>
          <div class=" col-span-6 pt-[2vh] pb-[4vh]">
            <div class="mt-4 rounded-lg drop-shadow bg-white grid grid-cols-5">

              <!-- Top Headline -->
              <div class=" col-span-5 bg-gradient-to-r from-[#017BBC] to-[#5F3395] rounded-t-lg">
                <p class=" text-3xl text-white text-left my-5 ml-10">Cancer Risk (AGE {{ageV}})</p>
              </div>
              <!-- 1st Headline -->
              <p class="mt-2 mb-3 text-center text-3xl text-[#623093] col-span-5">Your risk of developing Breast Cancer</p>

              <div class=" col-span-2 mx-5">
                <div class=" px-10">
                  <p class="text-left text-lg mb-1 font-bold">Track your risk evolution for the next decade</p>
                  <vue3-slider @change="Page03()" :alwaysShowHandle="true" v-model="age" :min="ageMin" :max="ageMax" :height="sliderHeight" color="#623093" :tooltip="true" track-color="#EEE5F7" />
                  <div class=" flex justify-between font-bold">
                    <span >Age {{ageMin}}</span>
                    <span >Age {{ageMax}}</span>
                  </div>
                </div>
                <p class=" text-slate-800 text-xl m-2">Your Risk at Age {{age}} until 80 is {{ageR}}%</p>
                <Doughnut :data="dataS" class="pb-4 max-h-[40vh]"/>
              </div>

              <div v-if="selectGraph==1" class=" col-span-3 mr-5">
                <div class="flex">
                  <button  class="p-1 bg-[#623093] w-full text-white hover:cursor-pointer border border-slate-500 rounded-l" >Your Lifetime Risk until Age 80</button>
                  <button @click="selectGraph=2" class="p-1 bg-[#FAF9F6] hover:bg-[#EEE5F7] w-full hover:cursor-pointer border border-slate-500" >Your Risk in Next 10 Years</button>
                </div>
                <div class="pt-10 pb-1">
                  <Bar :data="dataF"  />
                </div>
                <button @click="boxPlot1=true" class="underline text-[#623093] text-lg hover:scale-105 hover:cursor-pointer">View an in-depth graph</button>
                
              </div>
              <div v-else-if="selectGraph==2" class=" col-span-3 mr-5">
                <div class="flex">
                  <button @click="selectGraph=1" class="p-1 bg-[#FAF9F6] hover:bg-[#EEE5F7] w-full hover:cursor-pointer border border-slate-500 rounded-l" >Your Lifetime Risk until Age 80</button>
                  <button class="p-1 bg-[#623093] w-full text-white hover:cursor-pointer border border-slate-500" >Your Risk in Next 10 Years</button>
                </div>
                <div class="pt-10 pb-1">
                  <Bar :data="dataF2"  />
                </div>
                <button @click="boxPlot2=true" class="underline text-[#623093] text-lg hover:scale-105 hover:cursor-pointer">View an in-depth graph</button>
              </div>

              <div class=" col-span-5 text-left px-20 my-8 text-black leading-7">
                <p class=" font-bold">Graph explanation:</p>
                <p class=" pl-10"><span class="pr-2">&#x2022;</span>At age {{age}}, There is a {{ageR}}% risk that you will develop breast cancer by the age of 80 years.</p>
                <p v-if="ageRL!=0 || ageRU!=0" class="pl-10"><span class="pr-2">&#x2022;</span>Your risk in next 10 years is: {{ageRL}}%-{{ageRU}}%</p>
                <p v-else class="pl-10"><span class="pr-2">&#x2022;</span>Your risk in next 10 years is 0%</p>
              </div>

              <div class="mx-10 p-2 col-span-5 bg-gradient-to-r from-[#017BBC] to-[#5F3395] rounded-lg grid grid-cols-5">
                <div class=" col-span-5" v-if="!boolean1 && !boolean2">
                  <p class=" text-white text-xl p-1">Have you diagnosed with breast cancer Before?</p>
                  <div class="pb-1" role="group">
                    <button @click="boolean1=true;boolean2=false; NewRisk()" :class="{ activebool: boolean1 }" class=" text-slate-800 px-3 py-1 bg-slate-100 hover:bg-orange-400 rounded m-1">Yes</button>
                    <button @click="boolean1=false;boolean2=true" :class="{ activebool: boolean2 }" class=" text-slate-800 px-3 py-1 bg-slate-100 hover:bg-orange-400 rounded m-1">No</button>
                  </div>
                </div>
                <div v-if="boolean2" class=" flex items-center justify-center col-span-5">
                  <p class="px-10 text-lg text-white">Same as upper result</p>
                </div>
                <div v-if="boolean1" class=" flex items-center justify-center col-span-4">
                  <p class="px-10 text-lg text-white">Then, You have redused the risk of getting diagnosed with cancer by 90%, your new risk is {{boolean1Value}}%</p>
                </div>
                <div v-if="boolean1" class=" flex items-center justify-start col-span-1">  
                  <div class=" max-w-fit bg-white rounded-3xl drop-shadow">
                    <Doughnut :data="dataBoolean1" class="pb-4 max-h-[25vh] text-white"/>
                  </div>
                </div>
              </div>

              <!-- border line -->
              <div class=" col-span-5 border mx-10 my-8 border-gray-300"></div>
              
              <!-- 2nd Headline -->
              <p class=" mb-5 text-center text-3xl text-[#623093] col-span-5">Your risk of developing Ovarian Cancer</p>
              
              <div class=" col-span-2 mx-5"> 
                <div class=" px-10">
                  <p class="text-left text-lg mb-1 font-bold">Track your risk evolution for the next decade</p>
                  <vue3-slider @change="Page04()" :alwaysShowHandle="true" v-model="age2" :min="ageMin" :max="ageMax" :height="sliderHeight" color="#623093" :tooltip="true" track-color="#EEE5F7" />
                 <div class=" flex justify-between font-bold">
                    <span >Age {{ageMin}}</span>
                    <span >Age {{ageMax}}</span>
                  </div>
                </div>
                <p class=" text-slate-800 text-xl m-2 ">Your Risk at Age {{age2}} until 80 is {{ageR2}}%</p>
                <Doughnut :data="dataS2" class="pb-4 max-h-[40vh]"/>
              </div>

              <div v-if="selectGraph2==1" class=" col-span-3 mr-5">
                <div class="flex">
                  <button  class="p-1 bg-[#623093] w-full text-white hover:cursor-pointer border border-slate-500 rounded-l" >Your Lifetime Risk until Age 80</button>
                  <button @click="selectGraph2=2" class="p-1 bg-[#FAF9F6] hover:bg-[#EEE5F7] w-full hover:cursor-pointer border border-slate-500 rounded-r" >Your Risk in Next 10 Years</button>
                  </div>
                <div class="pt-10 pb-1"><Bar :data="dataJ"  /></div>
                <button @click="boxPlot3=true" class="underline text-[#623093] text-lg hover:scale-105 hover:cursor-pointer">View an in-depth graph</button>
                
              </div>
              <div v-else-if="selectGraph2==2" class=" col-span-3 mr-5">
                <div class="flex">
                  <button @click="selectGraph2=1" class="p-1 bg-[#FAF9F6] hover:bg-[#EEE5F7] w-full hover:cursor-pointer border border-slate-500 rounded-l" >Your Lifetime Risk until Age 80</button>
                  <button class="p-1 bg-[#623093] w-full text-white hover:cursor-pointer border border-slate-500 rounded-r" >Your Risk in Next 10 Years</button>
                 </div>
                <div class="pt-10 pb-1"><Bar :data="dataJ2"  /></div>
                <button @click="boxPlot4=true" class="underline text-[#623093] text-lg hover:scale-105 hover:cursor-pointer">View an in-depth graph</button>
                
              </div>

              <div class=" col-span-5 text-left px-20 my-8 text-black leading-7">
                <p class=" font-bold">Graph explanation:</p>
                <p class=" pl-10"><span class="pr-2">&#x2022;</span>At age {{age2}}, There is a {{ageR2}}% risk that you will develop breast cancer by the age of 80 years.</p>
                <p v-if="ageRL2!=0 || ageRU2!=0" class="pl-10"><span class="pr-2">&#x2022;</span>Your risk in next 10 years is: {{ageRL2}}%-{{ageRU2}}%</p>
                <p v-else class="pl-10"><span class="pr-2">&#x2022;</span>Your risk in next 10 years is 0%</p>
              </div>

              <div class="mx-10 p-2 col-span-5 bg-gradient-to-r from-[#017BBC] to-[#5F3395] rounded-lg grid grid-cols-5 mb-5">
                <div class=" col-span-5" v-if="!boolean3 && !boolean4">
                  <p class=" text-white text-xl p-1">Have you diagnosed with ovarin cancer Before?</p>
                  <div class="pb-1" role="group">
                    <button @click="boolean3=true;boolean4=false; NewRisk2()" :class="{ activebool: boolean3 }" class=" text-slate-800 px-3 py-1 bg-slate-100 hover:bg-orange-400 rounded m-1">Yes</button>
                    <button @click="boolean3=false;boolean4=true" :class="{ activebool: boolean4 }" class=" text-slate-800 px-3 py-1 bg-slate-100 hover:bg-orange-400 rounded m-1">No</button>
                  </div>
                </div>
                <div v-if="boolean4" class=" flex items-center justify-center col-span-5">
                  <p class="px-10 text-lg text-white">Same as upper result</p>
                </div>
                <div v-if="boolean3" class=" flex items-center justify-center col-span-4">
                  <p class="px-10 text-lg text-white">Then, You have redused the risk of getting diagnosed with cancer by 90%, your new risk is {{boolean2Value}}%</p>
                </div>
                <div v-if="boolean3" class=" flex items-center justify-start col-span-1">  
                  <div class=" max-w-fit bg-white rounded-3xl drop-shadow">
                    <Doughnut :data="dataBoolean2" class="pb-4 max-h-[25vh] text-white"/>
                  </div>
                </div>
              </div>

            </div>
          </div>
          <div class="col-span-1"></div>
        </div>
    </div>

    <div v-else-if="page==10" class=" h-[82vh] ">
      <div class=" min-h-full m-20">
        <div class="mt-2"><input class="mt-6" type="file" @change="onFileChange" /></div>
        <button class=" bg-cyan-500 py-1 px-4 rounded text-white" @click="PrintData()">Print</button>
      </div>
    </div>

    <div v-if="modalAge" class="opacity-90 fixed inset-0 z-40 bg-black"></div>
    <div v-if="modalAge" class="overflow-x-hidden overflow-y-auto fixed inset-0 z-50 outline-none focus:outline-none justify-center items-center flex">
      <div class="relative w-auto my-6 mx-auto max-w-[600px] h-[50vh]">
        <!--content-->
        <div class="border-0 rounded shadow-lg relative flex flex-col w-full bg-white outline-none focus:outline-none">
          <!--header-->
          <div class="flex justify-center p-5 border-b border-solid border-slate-200 rounded-t">
            <h3 class="text-2xl font-semibold text-[#51287B]">Change your Age</h3>
          </div>
          <!--body-->
          <div class="w-[600px] py-5">
            <div class="mb-[2vh]" >
              <input v-model="ageV2" type="number" class="text-center rounded py-5 px-10 font-bold ring-2 border-slate-500">
            </div>
            <div class="" >
              <p class=" text-black">*age must be between 20 to 80 years</p>
            </div>
          </div>
          <!--footer-->
          <div class="flex items-center justify-center p-6 border-t border-solid border-slate-200 rounded-b">
             <button @click="modalAge=false;ChageAge2()" :disabled="ageV2=='' || ageV2<20 || ageV2>80" class="drop-shadow text-white py-4 px-12 font-bold bg-[#623093] disabled:text-slate-400 disabled:bg-slate-800 mx-2 rounded hover:scale-105">Change Age</button>
          </div>
        </div>
      </div>
    </div>

    <div v-if="modalGraph" class="opacity-90 fixed inset-0 z-40 bg-black"></div>
    <div v-if="modalGraph" class="overflow-x-hidden overflow-y-auto fixed inset-0 z-50 outline-none focus:outline-none justify-center items-center flex">
      <div class="relative w-auto my-6 mx-auto max-w-[600px] h-[50vh]">
        <!--content-->
        <div class="border-0 rounded shadow-lg relative flex flex-col w-full bg-white outline-none focus:outline-none">
          <!--header-->
          <div class="flex justify-center p-5 border-b border-solid border-slate-200 rounded-t">
            <h3 class="text-2xl font-semibold text-[#51287B]">Change gene</h3>
          </div>
          <!--body-->
          <div class="w-[600px] py-5">
            <div class="" role="group">
              <button @click="option1V=true; option3V=false; option4V=false; optionSelectV=true" type="button" :class="{ activeOpV: option1V }" class=" hover:scale-105 text-slate-100 drop-shadow hover:text-white py-3 px-10 font-bold bg-[#408dad] hover:bg-[#623093] mx-2 rounded">BRCA1</button>
              <button @click="option1V=false; option3V=true; option4V=false; optionSelectV=true" type="button" :class="{ activeOpV: option3V }" class=" hover:scale-105 text-slate-100 drop-shadow hover:text-white py-3 px-10 font-bold bg-[#408dad] hover:bg-[#623093] mx-2 rounded">BRCA2</button>
              <button @click="option1V=false; option3V=false; option4V=true; optionSelectV=true" type="button" :class="{ activeOpV: option4V }" class=" hover:scale-105 text-slate-100 drop-shadow hover:text-white py-3 px-10 font-bold bg-[#408dad] hover:bg-[#623093] mx-2 rounded">PALB2</button>
            </div>
          </div>
          <!--footer-->
          <div class="flex items-center justify-center p-6 border-t border-solid border-slate-200 rounded-b">
              <button @click="modalGraph=false;Page02V();ChageAge()" :disabled="!optionSelectV" class="drop-shadow text-white py-3 px-8 font-bold bg-[#623093] disabled:text-slate-400 disabled:bg-slate-800 mx-2 rounded hover:scale-105">Change GENE</button>
          </div>
        </div>
      </div>
    </div>

    <div v-if="boxPlot1" class="opacity-90 fixed inset-0 z-40 bg-black"></div>
    <div v-if="boxPlot1" class="overflow-x-hidden overflow-y-auto fixed inset-0 z-50 outline-none focus:outline-none justify-center items-center flex">
      <div class="relative my-6 mx-auto w-[68%]">
        <!--content-->
        <div class="border-0 rounded shadow-lg relative flex flex-col w-full h-full bg-white outline-none focus:outline-none">
          <!--header-->
          <div class="flex justify-between p-3 border-b border-solid border-slate-200 rounded-t">
            <h3 class="text-2xl font-semibold text-[#51287B]">Boxplot Graph</h3>
            <button @click="boxPlot1=false" class="drop-shadow text-white float-right py-1 px-6 font-bold bg-[#623093] disabled:text-slate-400 disabled:bg-slate-800 mx-2 rounded hover:scale-105">Close</button>
          </div>
          <!--body-->
          <div class="py-1">
            <apexchart type="boxPlot" class="" :options="chartOptions" :series="series"></apexchart>
          </div>
        </div>
      </div>
    </div>

    <div v-if="boxPlot2" class="opacity-90 fixed inset-0 z-40 bg-black"></div>
    <div v-if="boxPlot2" class="overflow-x-hidden overflow-y-auto fixed inset-0 z-50 outline-none focus:outline-none justify-center items-center flex">
      <div class="relative my-6 mx-auto w-[68%]">
        <!--content-->
        <div class="border-0 rounded shadow-lg relative flex flex-col w-full h-full bg-white outline-none focus:outline-none">
          <!--header-->
          <div class="flex justify-between p-3 border-b border-solid border-slate-200 rounded-t">
            <h3 class="text-2xl font-semibold text-[#51287B]">Boxplot Graph</h3>
            <button @click="boxPlot2=false" class="drop-shadow text-white float-right py-1 px-6 font-bold bg-[#623093] disabled:text-slate-400 disabled:bg-slate-800 mx-2 rounded hover:scale-105">Close</button>
          </div>
          <!--body-->
          <div class="py-1">
            <apexchart type="boxPlot" class="" :options="chartOptions" :series="series2"></apexchart>
          </div>
        </div>
      </div>
    </div>

    <div v-if="boxPlot3" class="opacity-90 fixed inset-0 z-40 bg-black"></div>
    <div v-if="boxPlot3" class="overflow-x-hidden overflow-y-auto fixed inset-0 z-50 outline-none focus:outline-none justify-center items-center flex">
      <div class="relative my-6 mx-auto w-[68%]">
        <!--content-->
        <div class="border-0 rounded shadow-lg relative flex flex-col w-full h-full bg-white outline-none focus:outline-none">
          <!--header-->
          <div class="flex justify-between p-3 border-b border-solid border-slate-200 rounded-t">
            <h3 class="text-2xl font-semibold text-[#51287B]">Boxplot Graph</h3>
            <button @click="boxPlot3=false" class="drop-shadow text-white float-right py-1 px-6 font-bold bg-[#623093] disabled:text-slate-400 disabled:bg-slate-800 mx-2 rounded hover:scale-105">Close</button>
          </div>
          <!--body-->
          <div class="py-1">
            <apexchart type="boxPlot" class="" :options="chartOptions" :series="series3"></apexchart>
          </div>
        </div>
      </div>
    </div>

    <div v-if="boxPlot4" class="opacity-90 fixed inset-0 z-40 bg-black"></div>
    <div v-if="boxPlot4" class="overflow-x-hidden overflow-y-auto fixed inset-0 z-50 outline-none focus:outline-none justify-center items-center flex">
      <div class="relative my-6 mx-auto w-[68%]">
        <!--content-->
        <div class="border-0 rounded shadow-lg relative flex flex-col w-full h-full bg-white outline-none focus:outline-none">
          <!--header-->
          <div class="flex justify-between p-3 border-b border-solid border-slate-200 rounded-t">
            <h3 class="text-2xl font-semibold text-[#51287B]">Boxplot Graph</h3>
            <button @click="boxPlot4=false" class="drop-shadow text-white float-right py-1 px-6 font-bold bg-[#623093] disabled:text-slate-400 disabled:bg-slate-800 mx-2 rounded hover:scale-105">Close</button>
          </div>
          <!--body-->
          <div class="py-1">
            <apexchart type="boxPlot" class="" :options="chartOptions" :series="series4"></apexchart>
          </div>
        </div>
      </div>
    </div>
   
   <!-- footer -->
    <div class=" h-[8vh] bottom-0 left-0 right-0 bg-gradient-to-r from-[#0577BA] to-[#603194]">
      <div class=" h-full w-full flex justify-center items-center">
      <p class=" text-white">© 2023 Western & Central Melbourne Integrated Cancer Service</p>
      </div>
    </div>
  </div>
</template>

<script >
// import LineChart from '../components/lineChart.ts';
import { Chart as ChartJS,
  RadialLinearScale,
  Tooltip,
  Legend,
  ArcElement,
  CategoryScale,
  LinearScale,
  BarElement,
  Title
} from 'chart.js'
import { Doughnut } from 'vue-chartjs'
import { PolarArea } from 'vue-chartjs'
import { Bar } from 'vue-chartjs'
import api from '../../boot/axios.js';
import readXlsxFile from 'read-excel-file';
import VueApexCharts from "vue3-apexcharts";
import slider from "vue3-slider"

ChartJS.register(ArcElement, Tooltip, Legend, RadialLinearScale, CategoryScale, LinearScale, BarElement, Title)
export default {
  components: {
    Doughnut ,PolarArea, Bar, apexchart: VueApexCharts, "vue3-slider": slider
  },
  data() {
    return {
      page:1,
      // page:5,
      option1:false,
      option3:false,
      option4:false,
      option1V:false,
      option3V:false,
      option4V:false,
      option11:false,
      option22:false,
      optionSelect:false,
      optionSelectV:false,
      optionSelect2:false,
      selectAge:1,
      selectAge2:1,
      selectGraph:1,
      selectGraph2:1,
      age:0,
      ageMin:20,
      ageMax:80,
      age2:0,
      ageV:0,
      ageV2:0,
      ageR:0,
      ageRU:'',
      ageRL:'',
      ageRU2:'',
      ageRL2:'',
      ageR2:'',
      sliderHeight:10,

      dataUpload:[],

      dataB1Breast:[],
      dataB1Ovarin:[],
      dataB2Breast:[],
      dataB2Ovarin:[],
      dataP2Breast:[],
      dataP2Ovarin:[],

      modalAge:false,
      modalGraph:false,
      boxPlot1:false,
      boxPlot2:false,
      boxPlot3:false,
      boxPlot4:false,

      boolean1:false,
      boolean3:false,
      boolean4:false,
      boolean1Value:0,
      boolean2:false,
      boolean2Value:0,

      dataF: {
        labels: [
          'Age 20-30',
          'Age 31-40',
          'Age 41-50',
          'Age 51-60',
          'Age 61-70',
          'Age 71-80',
        ],
        datasets: [
          {
            label: 'Your Risk until age 80',
            backgroundColor: ['#49A9B4'],
            pointBackgroundColor: '#009BBC',
            pointBorderColor: '#009BBC',
            pointHoverBackgroundColor: '#009BBC',
            pointHoverBorderColor: 'rgba(179,181,198,1)',
            data: []
          }
        ]
      },
      dataF2: {
        labels: [
          '20-30',
          '31-40',
          '41-50',
          '51-60',
          '61-70',
          '71-80',
        ],
        datasets: [
          {
            label: 'Your Risk in Next 10 Years',
            backgroundColor: ['#646FA9'],
            pointBackgroundColor: '#009BBC',
            pointBorderColor: '#009BBC',
            pointHoverBackgroundColor: '#009BBC',
            pointHoverBorderColor: 'rgba(179,181,198,1)',
            data: []
          },
        ]
      },
      dataJ: {
        labels: [
          'Age 20-30',
          'Age 31-40',
          'Age 41-50',
          'Age 51-60',
          'Age 61-70',
          'Age 71-80',
        ],
        datasets: [
          {
            label: 'Your Risk until age 80',
             backgroundColor: ['#048a96'],
            pointBackgroundColor: '#009BBC',
            pointBorderColor: '#009BBC',
            pointHoverBackgroundColor: '#009BBC',
            pointHoverBorderColor: 'rgba(179,181,198,1)',
            data: []
          },
        ]
      },
      dataJ2: {
        labels: [
          '20-30',
          '31-40',
          '41-50',
          '51-60',
          '61-70',
          '71-80',
        ],
        datasets: [
          {
            label: 'Your Risk in Next 10 Years',
            backgroundColor: ['#364382'],
            pointBackgroundColor: '#009BBC',
            pointBorderColor: '#009BBC',
            pointHoverBackgroundColor: '#009BBC',
            pointHoverBorderColor: 'rgba(179,181,198,1)',
            data: []
          },
        ]
      },
      dataS:{
        labels: ['No Risk', 'Risk'],
        datasets: [
          {
            backgroundColor: ['#23C552', '#F84F31'],
            data: []
          }
        ],
      },
      dataS2:{
        labels: ['No Risk', 'Risk'],
        datasets: [
          {
            backgroundColor: ['#23C552', '#F84F31'],
            data: []
          }
        ],
      },
      series: [
        {
          type: 'boxPlot',
          data:[]
        }
      ],
      series2: [
        {
          type: 'boxPlot',
          data:[]
        }
      ],
      series3: [
        {
          type: 'boxPlot',
          data:[]
        }
      ],
      series4: [
        {
          type: 'boxPlot',
          data:[]
        }
      ],
      chartOptions: {
        chart: {
          type: 'boxPlot',
        },
        plotOptions: {
          boxPlot: {
            colors: {
              upper: '#623093',
              lower: '#cfbce2'
            },
            responsive: [{
                breakpoint: undefined,
                options: {},
            }]
          }
        }
      },
      dataBoolean1:{
        labels: ['No Risk', 'Risk'],
        datasets: [
          {
            backgroundColor: ['#23C552', '#F84F31'],
            data: [40,60]
          }
        ],
      },
      dataBoolean2:{
        labels: ['No Risk', 'Risk'],
        datasets: [
          {
            backgroundColor: ['#23C552', '#F84F31'],
            data: [40,60]
          }
        ],
      },
      
    };
  },
  created() {
    this.getData();
  },
  methods: {
    async getData() {
      await api
        .get(`api/BRCA1Breast/`)
        .then((res) => {
          this.dataB1Breast = res.data
          // console.log(this.dataB1Breast.length);
        })
        .catch((error) => {
          console.log(error);
        });
      await api
        .get(`api/BRCA1Ovarin/`)
        .then((res) => {
          this.dataB1Ovarin = res.data
          // console.log(this.dataB1Ovarin.length);
        })
        .catch((error) => {
          console.log(error);
        });

      await api
        .get(`api/BRCA2Breast/`)
        .then((res) => {
          this.dataB2Breast = res.data
          // console.log(this.dataB2Breast.length);
        })
        .catch((error) => {
          console.log(error);
        });
      await api
        .get(`api/BRCA2Ovarin/`)
        .then((res) => {
          this.dataB2Ovarin = res.data
          // console.log(this.dataB2Ovarin.length);
        })
        .catch((error) => {
          console.log(error);
        });

      await api
        .get(`api/PALB2Breast/`)
        .then((res) => {
          this.dataP2Breast = res.data
          // console.log(this.dataP2Breast.length);
        })
        .catch((error) => {
          console.log(error);
        });
      await api
        .get(`api/PALB2Ovarin/`)
        .then((res) => {
          this.dataP2Ovarin = res.data
          // console.log(this.dataP2Ovarin.length);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    Page02V(){
      if (this.option1V) {
        this.option1=true
        this.option3=false
        this.option4=false
        this.Page02()
      }
      else if (this.option3V) {
        this.option1=false
        this.option3=true
        this.option4=false
        this.Page02()
      }
      else if (this.option4V) {
        this.option1=false
        this.option3=false
        this.option4=true
        this.Page02()
      }
      
    },
    Page02(){
      let dataV = []
      if (this.option1) {
        dataV = this.dataB1Breast
      } else if(this.option3){
        dataV = this.dataB2Breast
      } else if (this.option4) {
        dataV = this.dataP2Breast
      }
      let a = [0,0,0,0,0,0]
      let b = [0,0,0,0,0,0]
      for (let i = 0; i < dataV.length; i++) {
        if (dataV[i].age<=30) {
          a[0]+=parseFloat(dataV[i].averageLifetime)
          b[0]+=parseFloat(dataV[i].averageTen)
        }
        else if (dataV[i].age<=40) {
          a[1]+=parseFloat(dataV[i].averageLifetime)
          b[1]+=parseFloat(dataV[i].averageTen)
        }
        else if (dataV[i].age<=50) {
          a[2]+=parseFloat(dataV[i].averageLifetime)
          b[2]+=parseFloat(dataV[i].averageTen)
        }
        else if (dataV[i].age<=60) {
          a[3]+=parseFloat(dataV[i].averageLifetime)
          b[3]+=parseFloat(dataV[i].averageTen)
        }
        else if (dataV[i].age<=70) {
          a[4]+=parseFloat(dataV[i].averageLifetime)
          b[4]+=parseFloat(dataV[i].averageTen)
        }
        else {
          a[5]+=parseFloat(dataV[i].averageLifetime)
          b[5]+=parseFloat(dataV[i].averageTen)
        }
      }
      let x = [], x2 = []
      for (let i = 0; i < dataV.length; i++) {
        let z = {
          x: dataV[i].age,
          y: [
            parseInt(dataV[i].lowerCentileLifetime),
            (parseInt(dataV[i].averageLifetime)+parseInt(dataV[i].lowerCentileLifetime))/2,
            parseInt(dataV[i].averageLifetime),
            (parseInt(dataV[i].averageLifetime)+parseInt(dataV[i].upperCentileLifetime))/2,
            parseInt(dataV[i].upperCentileLifetime)
          ]
        }
        let z2 = {
          x: dataV[i].age,
          y: [
            parseInt(dataV[i].lowerCentile),
            (parseInt(dataV[i].averageTen)+parseInt(dataV[i].lowerCentile))/2,
            parseInt(dataV[i].averageTen),
            (parseInt(dataV[i].averageTen)+parseInt(dataV[i].upperCentile))/2,
            parseInt(dataV[i].upperCentile)
          ]
        }
        x.push(z)
        x2.push(z2)
      }
      this.series[0].data=x
      this.series2[0].data=x2
      for (let i = 0; i < a.length; i++) {
        if (i==0) {
          a[i] = (a[i]/11).toFixed(1)
          b[i] = (b[i]/11).toFixed(1)
        }
        else{
          a[i] = (a[i]/10).toFixed(1)
          b[i] = (b[i]/10).toFixed(1)
        }
      }
      this.dataF= {
        labels: [
          'Age 20-30',
          'Age 31-40',
          'Age 41-50',
          'Age 51-60',
          'Age 61-70',
          'Age 71-80',
        ],
        datasets: [
          {
            label: 'Your Risk until age 80',
            backgroundColor: ['#49A9B4'],
            pointBackgroundColor: '#009BBC',
            pointBorderColor: '#009BBC',
            pointHoverBackgroundColor: '#009BBC',
            pointHoverBorderColor: 'rgba(179,181,198,1)',
            data: a
          }
        ]
      }
      this.dataF2= {
        labels: [
          '20-30',
          '31-40',
          '41-50',
          '51-60',
          '61-70',
          '71-80',
        ],
        datasets: [
          {
            label: 'Your Risk in Next 10 Years',
            backgroundColor: ['#646FA9'],
            pointBackgroundColor: '#009BBC',
            pointBorderColor: '#009BBC',
            pointHoverBackgroundColor: '#009BBC',
            pointHoverBorderColor: 'rgba(179,181,198,1)',
            data: b
          },
        ]
      }

      dataV = []
      if (this.option1) {
        dataV = this.dataB1Ovarin
      } else if(this.option3){
        dataV = this.dataB2Ovarin
      } else if (this.option4) {
        dataV = this.dataP2Ovarin
      }
      a = [0,0,0,0,0,0]
      b = [0,0,0,0,0,0]
      for (let i = 0; i < dataV.length; i++) {
        if (dataV[i].age<=30) {
          a[0]+=parseFloat(dataV[i].averageLifetime)
          b[0]+=parseFloat(dataV[i].averageTen)
        }
        else if (dataV[i].age<=40) {
          a[1]+=parseFloat(dataV[i].averageLifetime)
          b[1]+=parseFloat(dataV[i].averageTen)
        }
        else if (dataV[i].age<=50) {
          a[2]+=parseFloat(dataV[i].averageLifetime)
          b[2]+=parseFloat(dataV[i].averageTen)
        }
        else if (dataV[i].age<=60) {
          a[3]+=parseFloat(dataV[i].averageLifetime)
          b[3]+=parseFloat(dataV[i].averageTen)
        }
        else if (dataV[i].age<=70) {
          a[4]+=parseFloat(dataV[i].averageLifetime)
          b[4]+=parseFloat(dataV[i].averageTen)
        }
        else {
          a[5]+=parseFloat(dataV[i].averageLifetime)
          b[5]+=parseFloat(dataV[i].averageTen)
        }
      }
      x = [], x2 = []
      for (let i = 0; i < dataV.length; i++) {
        let z = {
          x: dataV[i].age,
          y: [
            parseInt(dataV[i].lowerCentileLifetime),
            (parseInt(dataV[i].averageLifetime)+parseInt(dataV[i].lowerCentileLifetime))/2,
            parseInt(dataV[i].averageLifetime),
            (parseInt(dataV[i].averageLifetime)+parseInt(dataV[i].upperCentileLifetime))/2,
            parseInt(dataV[i].upperCentileLifetime)
          ]
        }
        let z2 = {
          x: dataV[i].age,
          y: [
            parseInt(dataV[i].lowerCentile),
            (parseInt(dataV[i].averageTen)+parseInt(dataV[i].lowerCentile))/2,
            parseInt(dataV[i].averageTen),
            (parseInt(dataV[i].averageTen)+parseInt(dataV[i].upperCentile))/2,
            parseInt(dataV[i].upperCentile)
          ]
        }
        x.push(z)
        x2.push(z2)
      }
      this.series3[0].data=x
      this.series4[0].data=x2


      for (let i = 0; i < a.length; i++) {
        if (i==0) {
          a[i] = (a[i]/11).toFixed(1)
          b[i] = (b[i]/11).toFixed(1)
        }
        else{
          a[i] = (a[i]/10).toFixed(1)
          b[i] = (b[i]/10).toFixed(1)
        }
      }

      this.dataJ= {
        labels: [
          'Age 20-30',
          'Age 31-40',
          'Age 41-50',
          'Age 51-60',
          'Age 61-70',
          'Age 71-80',
        ],
        datasets: [
          {
            label: 'Your Risk until age 80',
             backgroundColor: ['#048a96'],
            pointBackgroundColor: '#009BBC',
            pointBorderColor: '#009BBC',
            pointHoverBackgroundColor: '#009BBC',
            pointHoverBorderColor: 'rgba(179,181,198,1)',
            data: a
          },
        ]
      }
      this.dataJ2= {
        labels: [
          '20-30',
          '31-40',
          '41-50',
          '51-60',
          '61-70',
          '71-80',
        ],
        datasets: [
          {
            label: 'Your Risk in Next 10 Years',
            backgroundColor: ['#364382'],
            pointBackgroundColor: '#009BBC',
            pointBorderColor: '#009BBC',
            pointHoverBackgroundColor: '#009BBC',
            pointHoverBorderColor: 'rgba(179,181,198,1)',
            data: b
          },
        ]
      }
    },
    ChageAge(){
      this.selectAge=1
      this.selectAge2=1
      this.age=this.ageV
      this.age2=this.ageV
      this.ageMin = this.ageV
      this.ageMax = this.ageV+10
      if (this.ageMax>80) {
        this.ageMax=80
      }
      if (this.ageMin<20) {
        this.ageMin=20
      }
      this.Page03()
      this.Page04()
    },
    ChageAge2(){
      this.ageV=this.ageV2
      this.age=this.ageV
      this.age2=this.ageV
      this.ageMin = this.ageV
      this.ageMax = this.ageV+10
      if (this.ageMax>80) {
        this.ageMax=80
      }
      if (this.ageMin<20) {
        this.ageMin=20
      }
      this.selectAge=1
      this.selectAge2=1
      this.Page03()
      this.Page04()
    },
    NewRisk(){
      if(this.option1){
        for (let i = 0; i < this.dataB1Breast.length; i++) {
          if (this.dataB1Breast[i].age==this.ageV) {
            this.boolean1Value = (this.dataB1Breast[i].residualLifetime*0.1)
            this.boolean1Value = Math.round(this.boolean1Value * 10) / 10;
            this.dataBoolean1={
              labels: ['No Risk', 'Risk'],
              datasets: [
                {
                  backgroundColor: ['#23C552', '#F84F31'],
                  data: [100-this.boolean1Value,this.boolean1Value]
                }
              ],
            }
          }
        }
      }
      if(this.option3){
        for (let i = 0; i < this.dataB2Breast.length; i++) {
          if (this.dataB2Breast[i].age==this.ageV) {
            this.boolean1Value = (this.dataB2Breast[i].residualLifetime*0.1)
            this.boolean1Value = Math.round(this.boolean1Value * 10) / 10;
            this.dataBoolean1={
              labels: ['No Risk', 'Risk'],
              datasets: [
                {
                  backgroundColor: ['#23C552', '#F84F31'],
                  data: [100-this.boolean1Value,this.boolean1Value]
                }
              ],
            }
          }
        }
      }
      if(this.option4){
        for (let i = 0; i < this.dataP2Breast.length; i++) {
          if (this.dataP2Breast[i].age==this.ageV) {
            this.boolean1Value = (this.dataP2Breast[i].residualLifetime*0.1)
            this.boolean1Value = Math.round(this.boolean1Value * 10) / 10;
            this.dataBoolean1={
              labels: ['No Risk', 'Risk'],
              datasets: [
                {
                  backgroundColor: ['#23C552', '#F84F31'],
                  data: [100-this.boolean1Value,this.boolean1Value]
                }
              ],
            }
          }
        }
      }
    },
    NewRisk2(){
      if(this.option1){
        for (let i = 0; i < this.dataB1Ovarin.length; i++) {
          if (this.dataB1Ovarin[i].age==this.ageV) {
            this.boolean2Value = (this.dataB1Ovarin[i].residualLifetime*0.1)
            this.boolean2Value = Math.round(this.boolean2Value * 10) / 10;
            this.dataBoolean2={
              labels: ['No Risk', 'Risk'],
              datasets: [
                {
                  backgroundColor: ['#23C552', '#F84F31'],
                  data: [100-this.boolean2Value,this.boolean2Value]
                }
              ],
            }
          }
        }
      }
      if(this.option3){
        for (let i = 0; i < this.dataB2Ovarin.length; i++) {
          if (this.dataB2Ovarin[i].age==this.ageV) {
            this.boolean2Value = (this.dataB2Ovarin[i].residualLifetime*0.1)
            this.boolean2Value = Math.round(this.boolean2Value * 10) / 10;
            this.dataBoolean2={
              labels: ['No Risk', 'Risk'],
              datasets: [
                {
                  backgroundColor: ['#23C552', '#F84F31'],
                  data: [100-this.boolean2Value,this.boolean2Value]
                }
              ],
            }
          }
        }
      }
      if(this.option4){
        for (let i = 0; i < this.dataP2Ovarin.length; i++) {
          if (this.dataP2Ovarin[i].age==this.ageV) {
            this.boolean2Value = (this.dataP2Ovarin[i].residualLifetime*0.1)
            this.boolean2Value = Math.round(this.boolean2Value * 10) / 10;
            this.dataBoolean2={
              labels: ['No Risk', 'Risk'],
              datasets: [
                {
                  backgroundColor: ['#23C552', '#F84F31'],
                  data: [100-this.boolean2Value,this.boolean2Value]
                }
              ],
            }
          }
        }
      }
    },
    Page03(){
      if(this.option1){
        for (let i = 0; i < this.dataB1Breast.length; i++) {
          if (this.dataB1Breast[i].age==this.age) {
            this.ageR = (this.dataB1Breast[i].residualLifetime)
            this.ageR = Math.round(this.ageR * 10) / 10;
            this.dataS={
              labels: ['No Risk', 'Risk'],
              datasets: [
                {
                  backgroundColor: ['#23C552', '#F84F31'],
                  data: [100-this.ageR,this.ageR]
                }
              ],
            }

            this.ageRU = (this.dataB1Breast[i].upperCentile)
            this.ageRU = Math.round(this.ageRU * 10) / 10;

            this.ageRL = (this.dataB1Breast[i].lowerCentile)
            this.ageRL = Math.round(this.ageRL * 10) / 10;
          }
        }
      }
      if(this.option3){
        for (let i = 0; i < this.dataB2Breast.length; i++) {
          if (this.dataB2Breast[i].age==this.age) {
            this.ageR = (this.dataB2Breast[i].residualLifetime)
            this.ageR = Math.round(this.ageR * 10) / 10;
            this.dataS={
              labels: ['No Risk', 'Risk'],
              datasets: [
                {
                  backgroundColor: ['#23C552', '#F84F31'],
                  data: [100-this.ageR,this.ageR]
                }
              ],
            }

            this.ageRU = (this.dataB2Breast[i].upperCentile)
            this.ageRU = Math.round(this.ageRU * 10) / 10;

            this.ageRL = (this.dataB2Breast[i].lowerCentile)
            this.ageRL = Math.round(this.ageRL * 10) / 10;
          }
        }
      }
      if(this.option4){
        for (let i = 0; i < this.dataP2Breast.length; i++) {
          if (this.dataP2Breast[i].age==this.age) {
            this.ageR = (this.dataP2Breast[i].residualLifetime)
            this.ageR = Math.round(this.ageR * 10) / 10;
            this.dataS={
              labels: ['No Risk', 'Risk'],
              datasets: [
                {
                  backgroundColor: ['#23C552', '#F84F31'],
                  data: [100-this.ageR,this.ageR]
                }
              ],
            }

            this.ageRU = (this.dataP2Breast[i].upperCentile)
            this.ageRU = Math.round(this.ageRU * 10) / 10;

            this.ageRL = (this.dataP2Breast[i].lowerCentile)
            this.ageRL = Math.round(this.ageRL * 10) / 10;
          }
        }
      }
    },
    Page04(){
      if(this.option1){
        for (let i = 0; i < this.dataB1Ovarin.length; i++) {
          if (this.dataB1Ovarin[i].age==this.age2) {
            this.ageR2 = (this.dataB1Ovarin[i].residualLifetime)
            this.ageR2 = Math.round(this.ageR2 * 10) / 10;
            this.dataS2={
              labels: ['No Risk', 'Risk'],
              datasets: [
                {
                  backgroundColor: ['#23C552', '#F84F31'],
                  data: [100-this.ageR2,this.ageR2]
                }
              ],
            }

            this.ageRU2 = (this.dataB1Ovarin[i].upperCentile)
            this.ageRU2 = Math.round(this.ageRU2 * 10) / 10;

            this.ageRL2 = (this.dataB1Ovarin[i].lowerCentile)
            this.ageRL2 = Math.round(this.ageRL2 * 10) / 10;
          }
        }
      }
      if(this.option3){
        for (let i = 0; i < this.dataB2Ovarin.length; i++) {
          if (this.dataB2Ovarin[i].age==this.age2) {
            this.ageR2 = (this.dataB2Ovarin[i].residualLifetime)
            this.ageR2 = Math.round(this.ageR2 * 10) / 10;
            this.dataS2={
              labels: ['No Risk', 'Risk'],
              datasets: [
                {
                  backgroundColor: ['#23C552', '#F84F31'],
                  data: [100-this.ageR2,this.ageR2]
                }
              ],
            }

            this.ageRU2 = (this.dataB2Ovarin[i].upperCentile)
            this.ageRU2 = Math.round(this.ageRU2 * 10) / 10;

            this.ageRL2 = (this.dataB2Ovarin[i].lowerCentile)
            this.ageRL2 = Math.round(this.ageRL2 * 10) / 10;
          }
        }
      }
      if(this.option4){
        for (let i = 0; i < this.dataP2Ovarin.length; i++) {
          if (this.dataP2Ovarin[i].age==this.age2) {
            this.ageR2 = (this.dataP2Ovarin[i].residualLifetime)
            this.ageR2 = Math.round(this.ageR2 * 10) / 10;
            this.dataS2={
              labels: ['No Risk', 'Risk'],
              datasets: [
                {
                  backgroundColor: ['#23C552', '#F84F31'],
                  data: [100-this.ageR2,this.ageR2]
                }
              ],
            }

            this.ageRU2 = (this.dataP2Ovarin[i].upperCentile)
            this.ageRU2 = Math.round(this.ageRU2 * 10) / 10;

            this.ageRL2 = (this.dataP2Ovarin[i].lowerCentile)
            this.ageRL2 = Math.round(this.ageRL2 * 10) / 10;
          }
        }
      }
    },
    onFileChange(event) {
      let xlsxfile = event.target.files ? event.target.files[0] : null;
      readXlsxFile(xlsxfile).then((rows) => {
        console.log("rows:", rows.length)
        this.dataUpload = rows;
      });
    },
    async PrintData(){
      // console.log(this.dataUpload);
      for (let i = 1; i < this.dataUpload.length; i++) {
        let a= {
          "age": i+19,
          "averageTen": (this.dataUpload[i][0]*100).toFixed(6),
          "lowerCentile": (this.dataUpload[i][1]*100).toFixed(6),
          "upperCentile": (this.dataUpload[i][2]*100).toFixed(6),
          "averageLifetime": (this.dataUpload[i][3]*100).toFixed(6),
          "lowerCentileLifetime": (this.dataUpload[i][4]*100).toFixed(6),
          "upperCentileLifetime": (this.dataUpload[i][6]*100).toFixed(6),
          "residualLifetime": (this.dataUpload[i][5]*100).toFixed(6)
        }
        // console.table(a);
        await api
          .post(`api/PALB2Ovarin/`,a)
          .then((response) => {
            console.log(response);
          })
          .catch((error) => {
            console.log(error);
          });
      }
    }
  }
}
</script>
<style>
.activeOp {
  background: linear-gradient(to right, #E37C0A, #ED2D6C) !important;
  color: white !important;
}
.activeOpV {
  background: linear-gradient(to right, #E37C0A, #ED2D6C) !important;
  color: white !important;
}
.activeOp2 {
  background: linear-gradient(to right, #E37C0A, #ED2D6C) !important;
  color: white !important;
}
.activebool {
  background: linear-gradient(to right, #E37C0A, #ED2D6C) !important;
  color: white !important;
}
</style>
