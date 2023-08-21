<template>
    <div id="Screen2" v-show="showScreen2">
        <form id="fromScreen2">
            <fieldset>
                <h2>מחשבון תאריך הגשה</h2>
                <legend>בחר סוג פרויקט</legend>

                <!-- אזור בחירת סוג ספר -->
                <div id="selctBook">
                    <input type="radio" id="SeferTorah" name="item1" value="ספר תורה" v-model="userData.book" required />
                    <label for="SeferTorah">ספר תורה</label>
                    <input type="radio" id="Tfilin" name="item1" value="תפילין" v-model="userData.book" required />
                    <label for="Tfilin">תפילין</label>
                    <input type="radio" id="Mezuzot" name="item1" value="מזוזות" v-model="userData.book" required />
                    <label for="Mezuzot">מזוזות</label>
                    <input type="radio" id="MegilatEster" name="item1" value="מגילת אסתר" v-model="userData.book"
                        required />
                    <label for="MegilatEster">מגילת אסתר</label>
                    <input type="radio" id="SeferHaftarot" name="item1" value="ספר הפטרות" v-model="userData.book"
                        required />
                    <label for="SeferHaftarot">ספר הפטרות</label>
                    <input type="radio" id="Other" name="item1" value="אחר" v-model="userData.book" required />
                    <label for="Other">אחר</label>
                    <hr />
                </div>
                <!-- אזור בחירת נתונים נוספים -->
                <div class="row g-3">
                    <div class="col">
                        <label for="Amount"> הזן כמות </label>
                        <input type="number" min="1" id="Amount" v-model="userData.info.AmountSelct" />
                    </div>
                    <div class="col">
                        <label for="pages"> מספר עמודים (לספר 1) </label>
                        <input type="number"  id="pages" v-model="userData.info.pagesSelct" />
                    </div>
                </div>
                <div class="row g-3">
                    <div class="col">
                        <label for="profit"> רווח משוער </label>
                        <input type="number" id="profit" v-model="userData.info.profitSelct" />
                    </div>
                    <div class="col">

                        <label for="workHours">שעות עבודה ליום </label>
                        <input type="number" id="workHours" min="0" max="24" v-model="userData.info.workHoursSelct" />
                    </div>
                </div>
                <div class="row justify-content-md-center">
                    <div class="col-md-3">
                        <label for="speed">כמב עמודים אתה כותב בשעה?</label>
                        <input type="number" id="speed" required v-model="userData.info.speedSelct" />
                    </div>

                    <div class="col-md-3">
                        <label for="workInTzom"> עבודה בצומות</label>
                        <input type="checkbox" id="workInTzom" v-model="userData.info.workInTzom" />
                    </div>


                    <!-- הזנת ימי עבודה בשבוע -->

                    <div class="col-md-auto">
                        <h3>ימי עבודה בשבוע</h3>
                        <div class="row justify-content-md-center">
                            <div class="col-md-auto">
                                <input type="checkbox" id="workDay1" name="workDays" value="sunday"
                                    v-model="userData.workDays" />
                                <label for="workDay1">יום ראשון</label>
                            </div>
                            <div class="col-md-auto">
                                <input type="checkbox" id="workDay2" name="workDays" value="monday"
                                    v-model="userData.workDays" />
                                <label for="workDay2">יום שני</label>

                            </div>
                            <div class="col-md-auto">
                                <input type="checkbox" id="workDay3" name="workDays" value="tuesday"
                                    v-model="userData.workDays" />
                                <label for="workDay3">יום שלישי</label>
                            </div>
                            <div class="col-md-auto">
                                <input type="checkbox" id="workDay4" name="workDays" value="wednesday"
                                    v-model="userData.workDays" />
                                <label for="workDay4">יום רביעי</label>
                            </div>
                            <div class="col-md-auto">
                                <input type="checkbox" id="workDay5" name="workDays" value="thursday"
                                    v-model="userData.workDays" />
                                <label for="workDay5">יום חמישי</label>
                            </div>
                            <div class="col-md-auto">
                                <input type="checkbox" id="workDay6" name="workDays" value="friday"
                                    v-model="userData.workDays" />
                                <label for="workDay6">יום שישי</label>
                            </div>
                            <div class="col-md-auto">
                                <input type="checkbox" id="workDay7" name="workDays" value="saturday"
                                    v-model="userData.workDays" />
                                <label for="workDay7">מוצאי שבת</label>
                            </div>
                        </div>

                    </div>
                </div>
            </fieldset>
        </form>
        <button @click="startCalculator">חזור לשלב קודם</button>
        <button @click="submitScreen2">סיים וחשב</button>
    </div>
    <!-- מסך טעינה -->
    <div v-show="loader">
        <DotLoader />
    </div>
    <!-- מסך התוצאה -->
    <div v-show="showScreen3">
        <h1>פרויקט {{ userData.book }}</h1>
        <h1>תאריך ההגשה הוא {{ calculatData.DeadLinStr }}</h1>
        <h3>נתרו לך {{ calculatData.totalWorkDay }} ימי עבודה</h3>
        <h3>אתה צריך לכתוב {{ calculatData.pagePerDay.toFixed(1) }} דפים ליום</h3>
        <h3>הרווח המשוער הוא {{ calculatData.profitPerDay.toFixed(1) }} שקלים ליום</h3>
        <!-- <h3>אתה צריך לכתוב {{ calculatData.writePagePerHour.toFixed(1) }} דפים לשעה</h3> -->
        <!-- <ul>
            <li v-bind:ref_for="calculatData.holidayList in calculatData.holidayList"> {{ calculatData.holidayList }}</li>
        </ul> -->
        <ul v-bind:ref_for="calculatData.holidayList in calculatData.holidayList">
            {{ calculatData.holidayList }}
        </ul>
        <button @click="startCalculator">חישוב חדש</button>
    </div>
</template>
<script>
import DotLoader from "./DotLoader.vue";
export default {
    components: {
        DotLoader: DotLoader,
      
    },
    data() {
        return {
            //הגדרת תצוגת מסכים
            showScreen2: true,
            showScreen3: false,
            loader: false,

            userData: {
                book: [],
                info: {
                    AmountSelct: "",
                    dateSelct: "",
                    profitSelct: "",
                    pagesSelct: "",
                    workHoursSelct: "",
                    workInTzom: false,
                },
                workDays: [],
            },
            saveData: [], //לכאן ידחף כל נתוני המשתמש בלחיצה על כפתור החישוב
            calculatData: {
                RangeOfDates: [], //מערך המחיל טווח ימי העבודה
                newDate: "",  //תאריך נוכחי
                userDate: "", //תאריך הגשה
                JewishCalData: [], //מכיל נתונים מלוח העברי
                totalWorkDay: 0,
                pagePerDay: 0,
                profitPerDay: 0,
                writePagePerHour: 0,
                holidayList: [],
                tzom: "",
                pageSpeedPerOneDay: "",
                pageSpeedPerOneWeek: "",
                WeekWork: "",
                dayWork: 0,
                SumPages: "",
                EndDateTemp: "",
                holidayIn: 0,
                IdArry: 0,
                DeadLinStr: "",
            },
        };
    },
    methods: {
        // איפוס המחשבון
        startCalculator() {
      location.reload()
    },
        //מעבר לביצוע פעולות החישוב
        submitScreen2() {
            this.showScreen2 = !this.showScreen2;
            this.loader = !this.loader;
            this.saveData.push({ ...this.userData });
            this.powerFunc()
        },


        //קריאה לפונקציות הנדרשות
        async powerFunc() {
            this.pageSpeedPerOneDay() //חישוב מהירות כתיבת עמודים ליום
            this.pageSpeedPerOneWeek() //חישוב כמות עמודים לשבוע
            this.calSumPages() // חישוב כמות העמודים בפרויקט 
            this.calWeekWork() // חישוב שבועות העבודה
            this.calDayWork() // חישוב ימי העבודה
            this.calEndDate() //חישוב תאריך הגשה לפני פילטור חגים
            this.dayCalc() //הכנסת טווח ימי העבודה למערך
            let JewishCalData = await this.habcal() //קריאה לקבלת נתוני חגים
            this.holidayToList(JewishCalData) //דחיפת נתוני החגים למערך
            this.dayWork() //דחיפת ימי העבודה בשבוע למערך
            this.findHoliday() //מציאת חגים בטווח התאריכים
            await this.updateWorkDay()

        },
        pageSpeedPerOneDay() {
            this.calculatData.pageSpeedPerOneDay = (this.userData.info.speedSelct * this.userData.info.workHoursSelct)
            console.log(`מהירות כתיבה ${this.calculatData.pageSpeedPerOneDay}`);
        },
        pageSpeedPerOneWeek() {
            const workingDay = (this.userData.workDays.length)
            this.calculatData.pageSpeedPerOneWeek = (this.calculatData.pageSpeedPerOneDay * workingDay)
            console.log(`דפים לשבוע ${this.calculatData.pageSpeedPerOneWeek}`);
        },
        calSumPages() {
            this.calculatData.SumPages = (this.userData.info.pagesSelct * this.userData.info.AmountSelct)
            console.log(`כמות הדפים בפרויקט ${this.calculatData.SumPages}`);
        },
        calWeekWork() {
            this.calculatData.WeekWork = (this.calculatData.SumPages / this.calculatData.pageSpeedPerOneWeek)
            console.log(`שבועות עבודה ${this.calculatData.WeekWork}`);
        },
        calDayWork() {
            this.calculatData.dayWork = (this.calculatData.WeekWork * 7)
        },
        calEndDate() {
            let minWork = (this.calculatData.dayWork * 24 * 60)
            const date = new Date();
            date.setMinutes(date.getMinutes() + minWork);
            this.calculatData.EndDateTemp = date
            console.log(`תאריך הגשה ${date}`); // Date object representing the estimated submission date
        },

        /// התחלת פילטור ימי חג

        dayCalc() {
            const today = new Date();
            const dateUser = new Date(this.calculatData.EndDateTemp);
            console.log(` התחלה הוא ${today}`);
            console.log(` ההגשה הוא ${dateUser}`);
            //הכנסת טווח התאריכים למערך
            let ustart = today.getTime();
            let uend = dateUser.getTime();
            console.log(`התאריך ההגשה הוא ${uend}`);
            console.log(`התאריך התחלה  הוא ${ustart}`);
            while (ustart <= uend) {
                let thisDay = new Date(ustart);
                ustart += 86400000
                let DataStr = this.fixFormat(thisDay)
                this.calculatData.RangeOfDates[DataStr] = { workDay: false, holiday: false, holidayName: "" }
            }
        },

        async habcal() {
            let newDate = new Date();
            let newDataStr = this.fixFormat(newDate)
            let userDataStr = this.fixFormat(this.calculatData.EndDateTemp)
            let tzom = this.calculatData.tzom
            let response = await fetch(
                `https://www.hebcal.com/hebcal?cfg=json&v=1&${tzom}maj=on&start=${newDataStr}&end=${userDataStr}&lg=he`
            )
            let dayData = await response.json()
            this.calculatData.JewishCalData = dayData;
            return dayData;
        },

        holidayToList(JewishCalData) {
            let RangeOfDates = this.calculatData.RangeOfDates;
            let array = JewishCalData.items;
            for (let i = 0; i < array.length - 1; i++) {
                console.log(` ערך האי ${i}`);
                console.log(` התאריך הוא ${array}`);
                console.log(`ערך הלנט הוא  ${array.length}`);
                RangeOfDates[array[i].date].holiday = true;
                RangeOfDates[array[i].date].holidayName = array[i].hebrew;
            }
        },

        dayWork() {
            let today = new Date();
            let dateUser = new Date(this.calculatData.EndDateTemp);
            let array = this.calculatData.RangeOfDates;
            while (today <= dateUser) {
                let todayStr = this.fixFormat(today)

                //תנאי לבדיקה האם המשתמש בחר את היום כיום עבודה
                if (
                    this.userData.workDays.includes(today.toLocaleDateString("en-US", { weekday: "long" }).toLowerCase())
                ) {
                    array[todayStr].workDay = true;
                }
                today.setDate(today.getDate() + 1);
            }
        },

        findHoliday(IdArry = 0) {
            let RangeOfDates = this.calculatData.RangeOfDates
            let ChengeToArry = Object.keys(RangeOfDates)
            this.calculatData.holidayIn = 0 //איפוס מונה החגים
            for (let i = IdArry; i < ChengeToArry.length; i++) {
                console.log(`נתוני התנאי הם i = ${i} והמערך הוא ${ChengeToArry[i]}`);
                if (RangeOfDates[ChengeToArry[i]].holiday == true && RangeOfDates[ChengeToArry[i]].workDay == true) {
                    this.calculatData.holidayIn++
                    console.log("נמצא חג");
                }
                else {
                    console.log("בפילטר לא נמצא חג");
                }
            }
        },

        async updateWorkDay() {
            if (this.calculatData.holidayIn > 0) {
                this.calculatData.dayWork = (this.calculatData.dayWork + this.calculatData.holidayIn)
                this.calEndDate() //קריאה חוזרת לחישוב תאריך הגשה
                this.dayCalc() // קריאה לעדכון מערך טווח הימים
                let JewishCalData = await this.habcal() //קריאה לקבלת נתוני חגים
                this.holidayToList(JewishCalData) //דחיפת נתוני החגים למערך
                this.dayWork() //קריאה חוזרת לחישוב ימי עבודה בשבוע
                let RangeOfDates = this.calculatData.RangeOfDates
                let ChengeToArry = Object.keys(RangeOfDates)
                let IdArry = (ChengeToArry.length) //עדכון מספר האינדקס במערך למניעת ספירה חוזרת של חגים
                this.findHoliday(IdArry) //קריאה חוזרת לבדיקה האם יש חגים
                let holidayIn = this.calculatData.holidayIn
                console.log("jnnjnjnjjn");
                console.log(`הפונקציה נקראה בחזרה, ערך החגים הוא ${holidayIn} ערך האינדקס הוא ${IdArry} `);
                if (holidayIn > 0) {
                    this.updateWorkDay()
                }
              
            }

            else {
                console.log("לא נמצאו עוד חגים");
            }
            this.filterWorkDay() //הפעלת פונקציה לחישוב סופי של ימי עבודה
            this.profitPerDay() //חישוב רווח משוער ליום עבודה
            await this.DeadLinStr() //המרת תאריך הגשה לפורמט מתאים להצגה

        },

        //פילטור ימי עבודה שנתרו
        filterWorkDay() {
            let RangeOfDates = this.calculatData.RangeOfDates
            let ChengeToArry = Object.keys(RangeOfDates)
            for (let i = 0; i < ChengeToArry.length; i++) {
                if (RangeOfDates[ChengeToArry[i]].workDay == true && RangeOfDates[ChengeToArry[i]].holiday == false) {
                    this.calculatData.totalWorkDay++
                }
                else if (RangeOfDates[ChengeToArry[i]].workDay == true && RangeOfDates[ChengeToArry[i]].holiday == true) {
                    this.calculatData.holidayList.push(RangeOfDates[ChengeToArry[i]].holidayName)
                }
            }

        },

        async DeadLinStr(){
           let DeadLinStr = this.fixFormat(this.calculatData.EndDateTemp)
           let dateStr = new Date(DeadLinStr)
           let response = await fetch(
                `https://www.hebcal.com/converter?cfg=json&date=${DeadLinStr}&g2h=1&strict=1`
            )
            let dayData = await response.json()
           this.calculatData.DeadLinStr = `${dayData.hebrew}  ${dateStr.toLocaleDateString("en-GB")}`
        },

        //חישוב רווח משוער ליום עבודה
        profitPerDay() {
            let profit = (this.userData.info.profitSelct / this.calculatData.totalWorkDay)
            this.calculatData.profitPerDay = profit;
            this.loader = !this.loader;
            this.showScreen3 = !this.showScreen3;
        },



        //פונקצייה להמרת התאריך לפורמט מתאים לAPI
        fixFormat(date) {
            let dateStr = date.toLocaleDateString("en-GB");
            let DataStr = `${dateStr[6]}${dateStr[7]}${dateStr[8]}${dateStr[9]}-${dateStr[3]}${dateStr[4]}-${dateStr[0]}${dateStr[1]}`;
            return DataStr
        },


    }
}

</script>


