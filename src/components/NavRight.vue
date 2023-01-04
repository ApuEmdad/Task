<template>
  <link rel="stylesheet" href="./NavRight.css" />
  <div class="NavRight-container">
    <ul class="nested-dropdowns">
      <li class="NavRight-title">
        <div class="nested-dropdowns__item rectangle">
          <p>সংরক্ষন</p>

          <div>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24.618"
              height="13.984"
              viewBox="0 0 24.618 13.984"
            >
              <g id="filter" transform="translate(-1.166 -8.438)">
                <path
                  id="Path_27"
                  data-name="Path 27"
                  d="M24.58,10.906H2.37a1.234,1.234,0,0,1,0-2.468H24.58a1.234,1.234,0,0,1,0,2.468Z"
                  fill="#ec1c24"
                />
                <path
                  id="Path_28"
                  data-name="Path 28"
                  d="M21.979,18.781H8a1.234,1.234,0,0,1,0-2.468H21.979a1.234,1.234,0,0,1,0,2.468Z"
                  transform="translate(-1.512 -2.117)"
                  fill="#ec1c24"
                />
                <path
                  id="Path_29"
                  data-name="Path 29"
                  d="M18.858,26.656H14.745a1.234,1.234,0,0,1,0-2.468h4.113a1.234,1.234,0,0,1,0,2.468Z"
                  transform="translate(-3.326 -4.234)"
                  fill="#ec1c24"
                />
              </g>
            </svg>
          </div>
        </div>
        <ul>
          <li>
            <div class="nested-dropdowns__item item">See all</div>
          </li>

          <!-- pass the array here -->
          <div v-for="year in timeLine" :key="year.id">
            <li>
              <div class="nested-dropdowns__item item">{{ year.year }}</div>
              <ul class="months">
                <li v-for="month in year?.months" :key="month.lastDay">
                  {{ monthNames[new Date(month.lastDay).getMonth()] }}
                </li>
                <!--  <li v-for="month in year?.months" :key="month.lastDay">
                  {{ monthNames[new Date(month.lastDay).getMonth()] }}
                </li> -->
              </ul>
            </li>
          </div>

          <!-- Hard Coded -->
          <!--   <li>
            <div class="nested-dropdowns__item item">2018-2019</div>
            <ul class="months">
              <li>See all</li>
              <li>June 2018</li>
              <li>April 2018</li>
            </ul>
          </li>
          <li>
            <div class="nested-dropdowns__item item">2020-2021</div>
            <ul class="months">
              <li>See all</li>
              <li>December 2020</li>
              <li>September 2021</li>
            </ul>
          </li>
          <li>
            <div class="nested-dropdowns__item item">2022-2023</div>
            <ul class="months">
              <li>See all</li>
              <li>January 2022</li>
              <li>August 2022</li>
            </ul>
          </li> -->
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
const timeLineArray = () => {
  const firstDate = new Date("01/01/2019");
  const lastDate = new Date();

  const timeLine = [];
  let currentDate = firstDate;
  while (currentDate <= lastDate) {
    const year = currentDate.getFullYear();
    const month = currentDate.getMonth();

    let yearData = timeLine.find((yearData) => yearData.year === year);
    if (!yearData) {
      yearData = { id: timeLine.length + 1, year, months: [] };
      timeLine.push(yearData);
    }

    let monthData = yearData.months.find(
      (monthData) => monthData.month === month
    );
    if (!monthData) {
      monthData = { month, lastDay: "", firstDay: "" };
      yearData.months.push(monthData);
    }

    // Set the firstDay and lastDay of the month
    const lastDayOfMonth = new Date(year, month + 1, 0);
    const firstDayofMonth = new Date(year, month, 1);

    monthData.lastDay = `${
      lastDayOfMonth.getMonth() + 1
    }/${lastDayOfMonth.getDate()}/${year}`;
    monthData.firstDay = `${
      firstDayofMonth.getMonth() + 1
    }/${firstDayofMonth.getDate()}/${year}`;

    // Increment to the first lastDay of the next month
    currentDate.setMonth(month + 1);
    currentDate.setDate(1);

    // Check if the currentDate has exceeded the lastDate
    if (currentDate > lastDate) {
      break;
    }
  }

  return timeLine;
};

console.log(timeLineArray());

export default {
  name: "NavRight",

  created() {
    console.log(this.timeLine);
  },

  data() {
    return {
      /*       timeLine: [
        {
          id: 1,
          year: "2019",
          months: [
            {
              day: "01/31/2019",
            },
            {
              day: "02/28/2019",
            },
            {
              day: "03/31/2019",
            },
            {
              day: "04/30/2019",
            },
            {
              day: "05/31/2019",
            },
            {
              day: "06/30/2019",
            },
            {
              day: "07/31/2019",
            },
            {
              day: "08/31/2019",
            },
            {
              day: "09/30/2019",
            },
            {
              day: "10/31/2019",
            },
            {
              day: "11/30/2019",
            },
            {
              day: "12/31/2019",
            },
          ],
        },
        {
          id: 2,
          year: "2020",
          months: [
            {
              day: "01/31/2019",
            },
            {
              day: "02/28/2019",
            },
            {
              day: "03/31/2019",
            },
            {
              day: "04/30/2019",
            },
            {
              day: "05/31/2019",
            },
            {
              day: "06/30/2019",
            },
            {
              day: "07/31/2019",
            },
            {
              day: "08/31/2019",
            },
            {
              day: "09/30/2019",
            },
            {
              day: "10/31/2019",
            },
            {
              day: "11/30/2019",
            },
            {
              day: "12/31/2019",
            },
          ],
        },
        {
          id: 3,
          year: "2021",
          months: [
            {
              day: "01/31/2019",
            },
            {
              day: "02/28/2019",
            },
            {
              day: "03/31/2019",
            },
            {
              day: "04/30/2019",
            },
            {
              day: "05/31/2019",
            },
            {
              day: "06/30/2019",
            },
            {
              day: "07/31/2019",
            },
            {
              day: "08/31/2019",
            },
            {
              day: "09/30/2019",
            },
            {
              day: "10/31/2019",
            },
            {
              day: "11/30/2019",
            },
            {
              day: "12/31/2019",
            },
          ],
        },
        {
          id: 4,
          year: "2022",
          months: [
            {
              day: "01/31/2019",
            },
            {
              day: "02/28/2019",
            },
            {
              day: "03/31/2019",
            },
            {
              day: "04/30/2019",
            },
            {
              day: "05/31/2019",
            },
            {
              day: "06/30/2019",
            },
            {
              day: "07/31/2019",
            },
            {
              day: "08/31/2019",
            },
            {
              day: "09/30/2019",
            },
            {
              day: "10/31/2019",
            },
            {
              day: "11/30/2019",
            },
            {
              day: "12/31/2019",
            },
          ],
        },
        {
          id: 5,
          year: "2023",
          months: [
            {
              day: "01/31/2019",
            },
          ],
        },
      ], */

      timeLine: timeLineArray(),
      monthNames: [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ],
    };
  },

  methods: {},
};
</script>

<style>
.NavRight-container {
  display: flex;
  justify-content: right;
}
.nested-dropdowns {
  /* Border */
  border: 0.2px solid #d3cdcd;

  /* display: flex; */

  /* Reset list styles */
  list-style-type: none;
  margin: 0;
  padding: 0;
  width: 148px;
}

.nested-dropdowns li {
  cursor: pointer;

  /* Spacing */
  /* padding: 0.25rem; */

  /* Used to position the sub nested-dropdowns */
  position: relative;

  text-align: center;
}

/* The sub nested-dropdowns */
.nested-dropdowns ul {
  /* Border */
  /* border: 1px solid #d1d5db; */

  /* Hidden by default */
  display: none;

  /* Absolute position */
  left: 0;
  position: absolute;
  top: 100%;

  /* Reset styles */
  list-style-type: none;
  margin: 0;
  padding: 0;
}

/* The second level sub nested-dropdowns */
.nested-dropdowns ul ul {
  left: 100%;
  position: absolute;
  top: 0;
}

/* Change background color of list item when being hovered */

.nested-dropdowns li:hover {
  background-color: #343434;
  color: #fff;
}

.nested-dropdowns li:hover > div {
  color: #fff;
}
/* Show the direct sub nested-dropdowns when hovering the list item */
.nested-dropdowns li:hover > ul {
  display: block;
}

.rectangle {
  display: flex;
  justify-content: space-evenly;
  color: #ec1c24;
  font-size: 20px;
  font-weight: bold;
}

.item {
  border: 0.2px solid #d3cdcd;
  padding: 9px 0px;
  font-size: 16px;
  color: #343434;
  width: 148px;
}
.NavRight-title {
  padding: 0.25rem;
}

.months li {
  border: 0.2px solid #d3cdcd;
  padding: 9px 0px;
  font-size: 16px;
  color: #343434;
  width: 148px;
}
</style>
