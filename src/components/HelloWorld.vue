<template>
  <div class="array-date">
    <p>{{ secondLargest }} is the second largest value in the array</p>
  </div>
</template>

<script>
export default {
  name: "DemoProject",
  data() {
    return {
      students: [
        { name: "John", grade: 9, subjects: ["Math", "Science", "History"] },
        { name: "Alice", grade: 10, subjects: ["Math", "Biology", "Physics"] },
        {
          name: "Bob",
          grade: 11,
          subjects: ["Chemistry", "Physics", "Literature"],
        },
      ],
      unSortedArray: [2, 1, 7, 3, 8, 9, 4, 3]
    };
  },

  mounted() {
    console.log(this.transformStudents(this.students));
  },

  computed: {
    secondLargest() {
      let large = -Infinity;
      let secondLarge = -Infinity;
      
       for (let num of this.unSortedArray) {
        if (num > large) {
          secondLarge = large;
          large = num;
        } else if (num > secondLarge && num !== large) {
          secondLarge = num;
        }
      }
      return secondLarge !== -Infinity ? secondLarge : null;
    }
  },

  methods: {
    transformStudents(students) {
      const studentData = {};
      students.forEach((student) => {
        student.subjects.forEach((subject) => {
          if (!studentData[subject]) {
            studentData[subject] = [];
          }
          studentData[subject].push(student.name);
        });
      });
      return studentData;
    },
  },

  
};
</script>

