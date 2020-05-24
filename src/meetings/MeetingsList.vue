<template>
    <table v-if="meetings.length > 0">
        <thead>
        <tr>
            <th>Nazwa spotkania</th>
            <th>Opis</th>
			<th>Uczestnicy</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="meeting in meetings" :key="meeting.name">
            <td>{{ meeting.name }}</td>
            <td>{{ meeting.description }}</td>
			<td>
                <ul>
                    <li v-for="user in meeting.participants" :key="user">
                                {{user}}
                    </li>
                 </ul>
            </td>
            <td class="action-buttons">
                 <button id="enrollButton" class="button button-outline" @click="enroll(meeting)" v-if="meeting.participants.indexOf(username) < 0" >Zapisz się</button>
                 <button v-if="meeting.participants.length === 0" @click = "deleteMeeting(meeting)">Usuń puste spotkanie</button>
			</td>
        </tr>
        </tbody>
    </table>
		<div v-else>Brak zaplanowanych spotkań</div>
</template>

<script>
    export default {
        props: ['meetings','username'],
        methods: {
            enroll(meeting) {
                this.$emit('enrollToMeeting', meeting)
            },
            deleteMeeting(meeting) {
                this.$emit('delete', meeting);
            }
        }
		}
</script>

<style scoped>
    #enrollButton {
        margin-right: 5px;
    }
    td.action-buttons {
        text-align: right;
    }
</style>
