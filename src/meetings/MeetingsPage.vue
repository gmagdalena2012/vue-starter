<template>
    <div>
        <h2>Zajęcia</h2>
        <new-meeting-form v-if="showNewMeetingForm" @added="addNewMeeting($event)"></new-meeting-form>
        <button v-else @click="displayNewMeetingForm">Dodaj nowe spotkanie</button>
       <meetings-list :meetings="meetings" :username="user" @enrollToMeeting="addUserToMeeting($event)"
                       @delete="deleteMeeting($event)"></meetings-list>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
		props: ["user"],
        components: {NewMeetingForm, MeetingsList},
        data() {
            return {
                meetings: [],
				showNewMeetingForm: false
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);
				this.showNewMeetingForm = false;
            },
			 displayNewMeetingForm() {
                this.showNewMeetingForm = true;
			},	
			            addUserToMeeting(meeting) {
                meeting.participants.push(this.user);
            },
            deleteMeeting(meeting) {
                this.meetings.splice(this.meetings.indexOf(meeting), 1);

        }
    }
	}
</script>
