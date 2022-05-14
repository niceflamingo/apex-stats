<script lang="ts">
	const API_KEY = ''
	type PlayerData = {
		global: {
			name: string
			uid: number
		}
	}

	type MatchHistory = any

	async function initStats() {
		const response = await fetch(`https://api.mozambiquehe.re/bridge?auth=${API_KEY}&player=Cptn%20Coward&platform=X1`)
		const playerData: PlayerData = await response.json()
		const uid: number = playerData.global.uid
		const matchHistory: MatchHistory = await getMatchHistory(uid)

		console.log(matchHistory)
	}

	async function getMatchHistory(uid: number): Promise<MatchHistory> {
		const response = await fetch(`https://api.mozambiquehe.re/games?auth=${API_KEY}&uid=${uid}`)
		return await response.json()
	}

	initStats()
</script>

<h1>Welcome to Apex Stats</h1>

<!-- <style lang="scss">
</style>-->
