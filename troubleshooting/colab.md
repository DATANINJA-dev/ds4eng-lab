# When Colab misbehaves

Sorted by how often it actually happens in class.

---

### "My changes disappeared"

You were working on the shared copy instead of your own.

**Fix:** `File → Save a copy in Drive`, then work in that tab. Do this **first**,
before you run anything. The copy is yours, saves automatically, and lives in your
Drive under `Colab Notebooks/`.

---

### `NameError: name 'df' is not defined`

You ran a cell before the one that creates `df`. Colab does not care about the order
the cells are printed in — only the order you ran them.

**Fix:** `Runtime → Run all`. Then carry on from where you were.

---

### Everything was working, now nothing is

Your runtime was recycled. Colab disconnects after about 90 minutes idle and forgets
every variable.

**Fix:** `Runtime → Run all`. Nothing is lost — the notebook is the source of truth,
not the memory. This is exactly why every session reloads its data from this repo in
one line.

---

### The data will not load

The `load_data()` cell reads a public file over the internet.

- Check you are online, and that you are not on a network that blocks GitHub.
- `Runtime → Run all` to make sure the **⚙️ CONFIGURE** cell ran before it.
- If UPC wifi is fighting you, tether from your phone for the minute it takes.

---

### `KeyError: 'something'`

You asked for a column that does not exist — usually a typo or a capital letter.

**Fix:** run `df.columns` and copy the name exactly. Note that several columns in the
AI4I dataset contain their units in the name, brackets included:
`Air temperature [K]`, `Rotational speed [rpm]`, `Torque [Nm]`.

---

### `SettingWithCopyWarning`

A warning, not an error — your code ran. It is telling you that pandas is not certain
whether you meant to modify the original table or a slice of it.

**Fix:** be explicit. Use `df.loc[rows, "column"] = value`, or make a real copy with
`.copy()` when you slice.

---

### I have no laptop today

Pair up. Seriously — one screen between two people works better than you expect, and
the person reading the output out loud often learns more than the one typing.

---

### Nothing here matches my problem

Read the **last line** of the error message: Python puts the useful part at the
bottom. Paste it into Gemini and ask what it means. Then ask in the lab forum on
Atenea so everyone gets the answer.
