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
            <td>{{ meeting.description }}
			<td style="text-align: right">
                <button id="enrollButton" class="button button-outline">Zapisz się</button>
                <button>Usuń puste spotkanie</button>
            </td>
        </tr>
        </tbody>
    </table>
		<div v-else>Brak zaplanowanych spotkań</div>
</template>

<script>
    export default {
        props: ['meetings']
    }
</script>
