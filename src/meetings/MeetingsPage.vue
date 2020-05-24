<template>
    <div>
        <h2>Zajęcia</h2>
        <new-meeting-form v-if="showNewMeetingForm" @added="addNewMeeting($event)"></new-meeting-form>
        <button v-else @click="displayNewMeetingForm">Dodaj nowe spotkanie</button>
        <meetings-list :meetings="meetings"></meetings-list>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
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
            },
			 displayNewMeetingForm() {
                this.showNewMeetingForm = true;
			},	
			deleteMeeting(meeeting) {
                this.meetings.splice(this.meetings.indexOf(meeting),1);
            },
            addParticipantToMeeting(meeting){
                meeting.participants.push();
            },
            deleteParticipantFromMeeting(){
                meeting.participants.splice(meeting.participants.indexOf(this.email));
        }
    }
	}
</script>
