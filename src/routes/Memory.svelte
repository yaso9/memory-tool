<script lang="ts">
	let supercells: number;
	let wordWidth: number;
	let bankAddrWidth: number;
	let dimAAddrWidth: number;

	let numberBanks: number;
	let capacity: number;
	let dimASize: number;
	let numberDimA: number;
	let dimBAddrWidth: number;
	let dimBSize: number;
	let numberDimB: number;

	$: {
		numberBanks = 1 << bankAddrWidth;
		capacity = ((1 << 20) * supercells * wordWidth) / (1 << 20);
		dimASize = (capacity * (1 << 20)) / (1 << dimAAddrWidth) / numberBanks;
		numberDimA = 1 << dimAAddrWidth;
		dimBAddrWidth = Math.log2(((1 << 20) * supercells) / numberBanks / numberDimA);
		dimBSize = (capacity * (1 << 20)) / (1 << dimBAddrWidth) / numberBanks;
		numberDimB = 1 << dimBAddrWidth;
	}
</script>

<div class="container">
	<div class="row">
		<div class="col-6 offset-3">
			<div class="my-4 card">
				<div class="card-body">
					<h2>Memory</h2>

					<div class="mb-3">
						<label for="supercells" class="form-label"># Supercells</label>
						<div class="input-group">
							<input type="number" class="form-control" id="supercells" bind:value={supercells} />
							<span class="input-group-text">Mi (2^20)</span>
						</div>
					</div>

					<div class="mb-3">
						<label for="word-width" class="form-label">Word Width</label>
						<div class="input-group">
							<input type="number" class="form-control" id="word-width" bind:value={wordWidth} />
							<span class="input-group-text">bits</span>
						</div>
					</div>

					<div class="mb-3">
						<label for="bank-addr-width" class="form-label">Bank Address Width</label>
						<div class="input-group">
							<input
								type="number"
								class="form-control"
								id="bank-addr-width"
								bind:value={bankAddrWidth}
							/>
							<span class="input-group-text">bits</span>
						</div>
					</div>

					<div class="mb-3">
						<label for="dim-a-addr-width" class="form-label">
							Dim A Address Width (choose either rows or columns as Dim A)
						</label>
						<div class="input-group">
							<input
								type="number"
								class="form-control"
								id="dim-a-addr-width"
								bind:value={dimAAddrWidth}
							/>
							<span class="input-group-text">bits</span>
						</div>
					</div>

					<div class="mb-3">
						<label for="number-banks" class="form-label"># Banks</label>
						<input
							type="number"
							class="form-control"
							id="number-banks"
							bind:value={numberBanks}
							disabled
						/>
					</div>

					<div class="mb-3">
						<label for="dimASize" class="form-label">Capacity</label>
						<div class="input-group">
							<input
								type="number"
								class="form-control"
								id="dimASize"
								bind:value={capacity}
								disabled
							/>
							<span class="input-group-text">Mib (2^20 bits)</span>
						</div>
					</div>

					<div class="mb-3">
						<label for="dimASize" class="form-label">Dim A Size</label>
						<div class="input-group">
							<input
								type="number"
								class="form-control"
								id="dimASize"
								bind:value={dimASize}
								disabled
							/>
							<span class="input-group-text">bits</span>
						</div>
					</div>

					<div class="mb-3">
						<label for="number-dim-a" class="form-label"># Dim A</label>
						<input
							type="number"
							class="form-control"
							id="number-dim-a"
							bind:value={numberDimA}
							disabled
						/>
					</div>

					<div class="mb-3">
						<label for="dim-b-addr-width" class="form-label">Dim B Address Width</label>
						<div class="input-group">
							<input
								type="number"
								class="form-control"
								id="dim-b-addr-width"
								bind:value={dimBAddrWidth}
								disabled
							/>
							<span class="input-group-text">bits</span>
						</div>
					</div>

					<div class="mb-3">
						<label for="dimBSize" class="form-label">Dim B Size</label>
						<div class="input-group">
							<input
								type="number"
								class="form-control"
								id="dimBSize"
								bind:value={dimBSize}
								disabled
							/>
							<span class="input-group-text">bits</span>
						</div>
					</div>

					<div class="mb-3">
						<label for="number-dim-b" class="form-label"># Dim B</label>
						<input
							type="number"
							class="form-control"
							id="number-dim-b"
							bind:value={numberDimB}
							disabled
						/>
					</div>
				</div>
			</div>
		</div>
	</div>
</div>
