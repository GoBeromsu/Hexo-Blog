---
emoji: π
categories: language
title: λλ§μ μ±λ§λ€κΈ°
author: λ²μ
date: '2022-03-10 18:00:00'
tags: λΈλ‘κ·Έ
cover: 
description: circularview, kotlin, viewholder, Room, corutine
---

## ν΄,, λ΄ μκ°

- [μμ€ μ½λ λ νΌμ§ν°λ¦¬λ νμ΄νΌ λ§ν¬λ₯Ό λ°λΌκ°λ©΄ λ³Ό μ μλ€](https://github.com/GoBeromsu/Circular-Timer)

* μλ° μ½μ§μ λλ¬΄ ν΄λ²λ Έμ΄ μ’ λ°°μ΄ κ²λ€μ νμ€ν μλλ° κ°λ¨νκ² λ§λλ €λ μλμ λ€λ₯΄κ² μΈν°λ·μμ λ°°μ°λ€λ³΄λ λλ λͺ¨λ₯΄κ² μ μλμ§? νλ©΄ λ°μ΄ν°λ² μ΄μ€ λΏ λ§μλλΌ mvmm ν¨ν΄λ κ°μ΄ λ§ μ μ©νλ €κ³  νλ€λ³΄λ κ± λ¨Έλ¦¬κ° ν‘ ν°μ§ λ» νλ€.
* μ΄μ  Adapter κ°λμ νμ€ν μ κ² κ°λ€.
* lifecycle μ£ΌκΈ°λ μ λλ‘ λͺ¨λ₯΄λλ° μ΄ κ³³ μ  κ³³μμ λ°°μ΄ λ΄ μλͺ»μ΄λ€. ν΄
* λ¨Έλ¦¬λ μνκ²Έ μ λ¦¬λ ν  κ²Έ κΈ μ΄λ€.

## circular view

```kotlin

    // oncreateκ° λΆμ ν¨μλ μμ± λ  λ ν λ² μ€νλλ λ©μλμ΄λ€.
    // μ»€μ€νν λ·°λ₯Ό μ‘ν°λΉν°μ λΆμ΄κΈ° μν μ μ°©μ μ΄λ€

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): PlanAdapter.CustomViewHolder {
        val view = LayoutInflater.from(parent.context).inflate(R.layout.[xml νμΌ μ΄λ¦], parent, false)
        return CustomViewHolder(view)
    }

    // κ°μ²΄ λ¦¬μ€νΈμ κ°μλ₯Ό λ°ν
    override fun getItemCount(): Int {
        return [λͺ¨λΈ λλ κ°μ²΄].size
    }

    override fun onBindViewHolder(holder: PlanAdapter.CustomViewHolder, position: Int) {
    }
    class CustomViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView) {
      // λ μ΄μμ λ΄μ μ»΄ν¬λνΈλ€μ μ¬μ μ
      // circular viewμ λ  λ¬Έμ  λλ¬Έμ μΊμλ₯Ό μ΄μ©νκΈ° μν¨μ΄λΌκ³ λν¨
      // μμ¦μ μλλ‘μ΄λ extension λλ¬Έμ findviewid μμ¨λ λμ νλ³΅μ΄μ§
        var name = itemView.tv_name

    }
}
```

```kotlin
class MainActivity : AppCompatActivity() {

    private val newPlanActivityRequestCode = 1
    private lateinit var planViewModel: PlanViewModel

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val adapter = CustomAdapter(this)

        rv_planlist.adapter =adapter
        rv_planlist.layoutManager = LinearLayoutManager(this)

        planViewModel = ViewModelProvider(this,PlanViewModel.Factory(application)).get(PlanViewModel::class.java)

    }

}
```

- λ©μΈ μ‘ν°λΉν°μμλ λ§λ€μ΄μ§ μ΄λν°λ₯Ό λ©μΈ μν°λΉν°μ xmlμ listviewμ μ°κ²°νλ€
  - μλλ©΄ μ»€μ€ν μ΄λν°λ 3λ¨κ³λ₯Ό κ±°μΉλ€.
    - mainActivity xml -- mainActivity λ΄ circularview - circular viewμ λ€μ΄κ° κ°μ²΄
    - μ  κ°μ²΄λ₯Ό μκΈ° λ§λλ‘ μ¬μ μ νκΈ° λλ¬Έμ μ»€μ€ν μ΄λν°λΌκ³ νλ€
- LayoutMangerλ₯Ό μΈννλ©΄ λ!
  - μν©μ λ°λΌμ μ΄λν°μ λ°°μ΄ λ£μ΄μ λ·° κ΅¬ννλ μμ λ€ μλλ° DBκ° μμ΄μ μμ λ₯Ό λ°λΌνλ κ±΄ κ°λ¨νλ€
  - LayoutManagerλ 3κ° μλ€.

## Adapter λλ MainActivityκ° μλ κ³³μμ DB μ κ·Ό

- fragment μ°λ©΄ μ΄λ΄ μΌμ μμ κ±° κ°μλ°? κ³΅λΆκ° μ’ λͺ¨μλΌλ€

### interfaceλ₯Ό μ΄μ©νλ λ°©λ²

- λ Deleteλ₯Ό κ΅¬ννκΈ° μν΄ μ΄ λ°©λ²μ μ¬μ©νλ€. adapterμ delete λ²νΌ λ¦¬μ€λλ₯Ό λ£μ μκ°μ΄μκΈ° λλ¬Έμ΄λ€.

#### DeleteBtnListener

  ```kotlin
  interface DeleteBtnListener {
      fun deleteBtnClicked(plan:Plan)
  }
  ```

  μΈν°νμ΄μ€λ₯Ό μ μΈνκ³  μΈν°νμ΄μ€ λ΄μ μ¬μ©ν  λ©μλλ₯Ό μ μΈνλ€

#### MainActivity

  ```kotlin
  class MainActivity : AppCompatActivity(), DeleteBtnListener {

      private lateinit var planViewModel: PlanViewModel

  override fun onCreate(savedInstanceState: Bundle?) {

        // μ΄λν° μ μ
        adapter = PlanAdapter(this, this)
        // viewModelProviderλ‘ λͺ¨λΈ λ°μμ€κΈ°
        planViewModel = ViewModelProvider(this).get(PlanViewModel::class.java)

        planViewModel.allPlan.observe(this, Observer { plan ->
            plan?.let { adapter.setPlans(it) }
        })
    }

      override fun deleteBtnClicked(plan: Plan) {
          planViewModel.delete(plan)
      }
  }
  ```

- λ©μΈ μ‘ν°λΉν°μμλ μΈν°νμ΄μ€λ₯Ό λ°μ ν μΈν°νμ΄μ€ λ©μλλ₯Ό μ¬μ μ νλ€.
- λ©μλ deleteBtnClickedλ₯Ό λ³΄λ©΄ planViewModel μμμ μ μ μλ€.

- μ΄ viewModelμ λ©μΈ μ‘ν°λΉν°μμ μ μν΄μ μ­ μ¬μ©ν  viewModelμ΄λ€

  ```kotlin
  override fun onCreate(savedInstanceState: Bundle?) {
   adapter = PlanAdapter(this, this)
  }
  ```

  - onCreate κ°μ κ²½μ° μ‘ν°λΉν°κ° μμ±λ  λ μ²μ μ€νλλ λ©μλμ΄λ€
  - μλμμ λ§νκ² μ§λ§ PlanAdapterμμλ deleBtnListenerλ₯Ό μμλ°λλ° λ©μΈ μ‘ν°λΉν°μμ μ¬μ μ λ λ¦¬μ€λλ₯Ό μ°κ²°νλ κ²μ΄λ€.

#### Plan Adapter

```kotlin
class PlanAdapter(val context: Context, deletelistener: DeleteBtnListener) :RecyclerView.Adapter<PlanAdapter.Holder>() {
      private var DeleteBtnListener: DeleteBtnListener = deletelistener

     inner class Holder(itemView: View) : RecyclerView.ViewHolder(itemView) {

        val content = itemView.tv_context
        val timeProgress = itemView.progress
        val start = itemView.bt_start
        val reset = itemView.bt_reset
        val delete = itemView.bt_delete

        fun bind(plan: Plan) {
            content.text = plan.content

            timeProgress.setOnTouchListener(OnTouchListener { v, event -> true })

            delete.setOnClickListener(View.OnClickListener {
                DeleteBtnListener.deleteBtnClicked(plan)
                notifyDataSetChanged()
            })
        }
    }
}
```

- μ΄λ ν΄λμ€λ‘ holerκ° μμ±λ κ²μ λ³Ό μ μλλ° recyclerviewμμλ viewholderμ λ΄μμ λ·°μ λΏλ¦¬κΈ° λλ¬Έμ νμνλ€
- bind() λ©μλλ₯Ό λ³΄λ©΄ deleteBtnClicked()λ₯Ό μ¬μ©νλ κ²μ λ³Ό μ μλ€.
