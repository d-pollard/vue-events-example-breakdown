<template>
  <div>
    <table>
      <thead>
        <tr>
          <template v-if="false" v-for="(eventHeaders, i) in events.headers">
            <th :key="'header-' + i">{{eventHeaders.text}}</th>
          </template>
          <th>ID</th>
          <th>Photo</th>
          <th>Title</th>
          <th>Date</th>
          <th>Location</th>
          <th>Summary</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
          <template v-if="false" v-for="(event, i) in events.entries">
            <tr :key="'event-' + i">
              <td
                v-for="(eventHeaders, i) in events.headers"
                :key="'eventItem-' + i">
                {{ event[eventHeaders.value] }}
              </td>
            </tr>
          </template>
          <template v-for="(event, i) in events.entries">
            <tr :key="'event-' + i">
              <td>{{event.id}}</td>
              <td>
                <img :src="randomPicture()"/>
              </td>
              <td>{{event.title}}</td>
              <td>{{event.date}}</td>
              <td>{{event.location}}</td>
              <td>
                <EventSummary :event="event"/>
              </td>
            </tr>
          </template>
      </tbody>
    </table>
  </div>
</template>

<script>
import EventSummary from './EventSummary'

let globalCounter = 0
export default {
  name: 'Events',
  components: { EventSummary },
  data () {
    return {
      imgCnt: 0,
      events: {
        headers: [
          {
            text: 'ID',
            sortable: true,
            align: 'left',
            value: 'id'
          },
          {
            text: 'Title',
            sortable: true,
            align: 'left',
            value: 'title'
          },
          {
            text: 'Date',
            sortable: true,
            align: 'left',
            value: 'date'
          },
          {
            text: 'Location',
            sortable: true,
            align: 'left',
            value: 'location'
          },
          {
            text: 'Summary',
            sortable: true,
            align: 'left',
            value: 'summary'
          }
        ],
        entries: [
          {
            id: 1,
            title: 'Some Event',
            date: new Date().getUTCDate(),
            location: 'Copandaro',
            summary: 'Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum,Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum, a placerat nunc. Proin viverra diam mauris, a malesuada urna aliquam vel. Praesent a sem velit. Interdum et malesuada fames ac ante ipsum primis in faucibus. Proin nibh augue, aliquet ac enim et, elementum rutrum nisi. Sed vel quam ac quam pellentesque molestie et vel augue.'
          },
          { id: 2, title: 'Another Event', date: new Date().getUTCDate(), location: 'Chicago', summary: 'Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum, a placerat nunc. Proin viverra diam mauris, a malesuada urna aliquam vel. Praesent a sem velit. Interdum et malesuada fames ac ante ipsum primis in faucibus. Proin nibh augue, aliquet ac enim et, elementum rutrum nisi. Sed vel quam ac quam pellentesque molestie et vel augue.' },
          { id: 3, title: 'Long Event', date: new Date().getUTCDate(), location: 'Dubai', summary: 'Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum, a placerat nunc. Proin viverra diam mauris, a malesuada urna aliquam vel. Praesent a sem velit. Interdum et malesuada fames ac ante ipsum primis in faucibus. Proin nibh augue, aliquet ac enim et, elementum rutrum nisi. Sed vel quam ac quam pellentesque molestie et vel augue.' },
          { id: 4, title: 'Short Event', date: new Date().getUTCDate(), location: 'Rome', summary: 'Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum, a placerat nunc. Proin viverra diam mauris, a malesuada urna aliquam vel. Praesent a sem velit. Interdum et malesuada fames ac ante ipsum primis in faucibus. Proin nibh augue, aliquet ac enim et, elementum rutrum nisi. Sed vel quam ac quam pellentesque molestie et vel augue.' },
          { id: 5, title: 'Avb Event', date: new Date().getUTCDate(), location: 'New York', summary: 'Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum, a placerat nunc. Proin viverra diam mauris, a malesuada urna aliquam vel. Praesent a sem velit. Interdum et malesuada fames ac ante ipsum primis in faucibus. Proin nibh augue, aliquet ac enim et, elementum rutrum nisi. Sed vel quam ac quam pellentesque molestie et vel augue.' },
          { id: 6, title: 'Lorem Event', date: new Date().getUTCDate(), location: 'Dallas', summary: 'Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum, a placerat nunc. Proin viverra diam mauris, a malesuada urna aliquam vel. Praesent a sem velit. Interdum et malesuada fames ac ante ipsum primis in faucibus. Proin nibh augue, aliquet ac enim et, elementum rutrum nisi. Sed vel quam ac quam pellentesque molestie et vel augue.' },
          { id: 7, title: 'Ipsum Event', date: new Date().getUTCDate(), location: 'Los Angeles', summary: 'Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum, a placerat nunc. Proin viverra diam mauris, a malesuada urna aliquam vel. Praesent a sem velit. Interdum et malesuada fames ac ante ipsum primis in faucibus. Proin nibh augue, aliquet ac enim et, elementum rutrum nisi. Sed vel quam ac quam pellentesque molestie et vel augue.' },
          { id: 8, title: 'Evelum Event', date: new Date().getUTCDate(), location: 'Seattle', summary: 'Morbi cursus efficitur augue et molestie. Nulla nec maximus ipsum. In vestibulum tincidunt ipsum, a placerat nunc. Proin viverra diam mauris, a malesuada urna aliquam vel. Praesent a sem velit. Interdum et malesuada fames ac ante ipsum primis in faucibus. Proin nibh augue, aliquet ac enim et, elementum rutrum nisi. Sed vel quam ac quam pellentesque molestie et vel augue.' }
        ]
      }
    }
  },
  methods: {
    randomPicture (x = 100, y = 60) {
      globalCounter++
      return `https://placeimg.com/${x}/${y}/any?date=${new Date().getMilliseconds()}&i${globalCounter}=${globalCounter}`
    }
  }
}
</script>

<style scoped>
  table, th, td {
    border: 1px solid black;
  }
</style>
